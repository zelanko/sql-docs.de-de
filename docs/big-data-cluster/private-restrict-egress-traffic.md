---
title: Einschränken des ausgehenden Datenverkehrs von Big Data-Clustern (BDC) in einem privaten Azure Kubernetes Service-Cluster (AKS-Cluster)
titleSuffix: SQL Server Big Data Clusters
description: Erfahren Sie, wie Sie den ausgehenden Datenverkehr von Big Data-Clustern (BDC) in einem privaten Azure Kubernetes Service-Cluster (AKS-Cluster) einschränken.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 08/20/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 962e155b3b0b5906d36fa4d884be2af353cb25a9
ms.sourcegitcommit: 1126792200d3b26ad4c29be1f561cf36f2e82e13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90076608"
---
# <a name="restrict-egress-traffic-of-big-data-clusters-bdc-clusters-in-azure-kubernetes-service-aks-private-cluster"></a>Einschränken des ausgehenden Datenverkehrs von Big Data-Clustern (BDC) in einem privaten Azure Kubernetes Service-Cluster (AKS-Cluster)

AKS stellt eine Standard-SKU-Lastenausgleichsressource bereit, die für ausgehenden Datenverkehr standardmäßig eingerichtet und verwendet wird. Das Standardsetup erfüllt aber möglicherweise nicht alle Anforderungen in allen Szenarien, wenn öffentliche IP-Adressen nicht zulässig oder zusätzliche Hops für den ausgehenden Datenverkehr erforderlich sind. Definieren Sie eine benutzerdefinierte Routingtabelle, wenn der Cluster keine öffentlichen IP-Adressen zulässt und sich hinter einem virtuellen Netzwerkgerät (Network Virtual Appliance, NVA) befindet.

Zu Verwaltungs- und operativen Zwecken verfügen AKS-Cluster standardmäßig über uneingeschränkten ausgehenden Internetzugriff. Die Workerknoten in einem AKS-Cluster müssen auf bestimmte Ports und vollqualifizierte Domänennamen (Fully Qualified Domain Names, FQDNs) zugreifen. Beispiele:

* Betriebssystem-Sicherheitsupdates für Workerknoten: Der Cluster muss Containerimages des Basissystems aus der Microsoft-Containerregistrierung (Microsoft Container Registry, MCR) abrufen.
* GPU-fähige AKS-Workerknoten müssen auf einige Endpunkte von Nvidia zugreifen, um Treiber zu installieren.
* Szenario, in dem Kunden AKS-Workerknoten in Verbindung mit Azure-Diensten wie Azure Policy für die Konformität auf Unternehmensebene oder Azure Monitoring (mit Container Insights) verwenden 
* Dev Spaces aktiviert und weitere ähnliche Szenarien

> [!NOTE]
> Beim Bereitstellen von BDC in einem privaten Azure Kubernetes Service-Cluster (AKS-Cluster) bestehen derzeit in diesem Szenario keine eingehenden Abhängigkeiten, außer den in diesem Artikel erwähnten. Alle ausgehenden Abhängigkeiten finden Sie unter [Steuern des ausgehenden Datenverkehrs für Clusterknoten in Azure Kubernetes Service (AKS)](/azure/aks/limit-egress-traffic).

In diesem Artikel wird das Bereitstellen von BDC in einem privaten AKS-Cluster mit erweiterten Netzwerkeinstellungen und UDR (User-Defined Route, benutzerdefinierte Route) beschrieben, und es wird die weitere Integration in eine Unternehmensnetzwerkumgebung erörtert.

## <a name="use-azure-firewall-to-restrict-egress-traffic"></a>Einschränken des ausgehenden Datenverkehrs mithilfe von Azure Firewall

Azure Firewall bietet ein FQDN-Tag für Azure Kubernetes Service `(AzureKubernetesService)`, um diese Konfiguration zu vereinfachen.

Ausführliche Informationen zu diesem Tag finden Sie unter [Einschränken von ausgehendem Datenverkehr mithilfe von Azure Firewall](/azure/aks/limit-egress-traffic#restrict-egress-traffic-using-azure-firewall).

In der folgenden Abbildung ist dargestellt, wie der Datenverkehr in einem privaten AKS-Cluster eingeschränkt wird. 

:::image type="content" source="media/private-cluster-restrict-egress-traffic/aks-azure-firewall-egress.png" alt-text="Ausgehender Datenverkehr des privaten AKS-Clusters – Azure Firewall":::

Gehen Sie wie folgt vor, um eine Basisarchitektur mit Azure Firewall einzurichten:

1. Erstellen der Ressourcengruppe und des VNets
2. Erstellen und Einrichten von Azure Firewall
3. Erstellen einer benutzerdefinierten Routingtabelle
4. Einrichten von Firewallregeln
5. Erstellen des Dienstprinzipals (Service Principal, SP)
6. Erstellen des privaten AKS-Clusters
7. Erstellen eines BDC-Bereitstellungsprofils
8. Bereitstellen von BDC

In den folgenden Schritten finden Sie die Details.

## <a name="create-the-resource-group-and-vnet"></a>Erstellen der Ressourcengruppe und des VNets

1. Definieren Sie eine Reihe von Umgebungsvariablen für das Erstellen von Ressourcen.

   ```console
   export REGION_NAME=<region>
   export RESOURCE_GROUP=private-bdc-aksudr-rg
   export SUBNET_NAME=aks-subnet
   export VNET_NAME=bdc-vnet
   export AKS_NAME=bdcaksprivatecluster
   ```

1. Ressourcengruppe erstellen

   ```azurecli
   az group create -n $RESOURCE_GROUP -l $REGION_NAME
   ```

1. Erstellen des VNets

   ```azurecli
   az network vnet create \
     --resource-group $RESOURCE_GROUP \
     --location $REGION_NAME \
     --name $VNET_NAME \
     --address-prefixes 10.0.0.0/8 \
     --subnet-name $SUBNET_NAME \
     --subnet-prefix 10.1.0.0/16

   SUBNET_ID=$(az network vnet subnet show \
     --resource-group $RESOURCE_GROUP \
     --vnet-name $VNET_NAME \
     --name $SUBNET_NAME \
     --query id -o tsv)
   ```

## <a name="create-and-set-up-azure-firewall"></a>Erstellen und Einrichten von Azure Firewall

1. Definieren Sie eine Reihe von Umgebungsvariablen für das Erstellen von Ressourcen.

   ```console
   export FWNAME=bdcaksazfw
   export FWPUBIP=$FWNAME-ip
   export FWIPCONFIG_NAME=$FWNAME-config

   az extension add --name azure-firewall
   ```

1. Erstellen eines dedizierten Subnetzes für die Firewall

   > [!NOTE]
   > Der Firewallname kann nach der Erstellung nicht mehr geändert werden.

   ```azurecli
   az network vnet subnet create \
     --resource-group $RESOURCE_GROUP \
     --vnet-name $VNET_NAME \
     --name AzureFirewallSubnet \
     --address-prefix 10.3.0.0/24

    az network firewall create -g $RESOURCE_GROUP -n $FWNAME -l $REGION_NAME --enable-dns-proxy true

    az network public-ip create -g $RESOURCE_GROUP -n $FWPUBIP -l $REGION_NAME --sku "Standard"

    az network firewall ip-config create -g $RESOURCE_GROUP -f $FWNAME -n $FWIPCONFIG_NAME --public-ip-address $FWPUBIP --vnet-name $VNET_NAME
   ```

Standardmäßig wird der Datenverkehr zwischen Azure-Subnetzen, virtuellen Netzwerken und lokalen Netzwerken von Azure automatisch geroutet. 

## <a name="create-user-defined-route-table"></a>Erstellen einer benutzerdefinierten Routingtabelle

Erstellen Sie eine benutzerdefinierte Routingtabelle (User-Defined Route, UDR) mit einem Hop zu Azure Firewall.

```azurecli

export SUBID= <your Azure subscription ID>
export FWROUTE_TABLE_NAME=bdcaks-rt
export FWROUTE_NAME=bdcaksroute
export FWROUTE_NAME_INTERNET=bdcaksrouteinet

export FWPUBLIC_IP=$(az network public-ip show -g $RESOURCE_GROUP -n $FWPUBIP --query "ipAddress" -o tsv)
export FWPRIVATE_IP=$(az network firewall show -g $RESOURCE_GROUP -n $FWNAME --query "ipConfigurations[0].privateIpAddress" -o tsv)

# Create UDR and add a route for Azure Firewall

az network route-table create -g $RESOURCE_GROUP --name $FWROUTE_TABLE_NAME

az network route-table route create -g $RESOURCE_GROUP --name $FWROUTE_NAME --route-table-name $FWROUTE_TABLE_NAME --address-prefix 0.0.0.0/0 --next-hop-type VirtualAppliance --next-hop-ip-address $FWPRIVATE_IP --subscription $SUBID

az network route-table route create -g $RESOURCE_GROUP --name $FWROUTE_NAME_INTERNET --route-table-name $FWROUTE_TABLE_NAME --address-prefix $FWPUBLIC_IP/32 --next-hop-type Internet
```

## <a name="set-up-firewall-rules"></a>Einrichten von Firewallregeln 

```azurecli
# Add FW Network Rules

az network firewall network-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwnr' -n 'apiudp' --protocols 'UDP' --source-addresses '*' --destination-addresses "AzureCloud.$REGION_NAME" --destination-ports 1194 --action allow --priority 100
az network firewall network-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwnr' -n 'apitcp' --protocols 'TCP' --source-addresses '*' --destination-addresses "AzureCloud.$REGION_NAME" --destination-ports 9000
az network firewall network-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwnr' -n 'time' --protocols 'UDP' --source-addresses '*' --destination-fqdns 'ntp.ubuntu.com' --destination-ports 123

# Add FW Application Rules

az network firewall application-rule create -g $RESOURCE_GROUP -f $FWNAME --collection-name 'aksfwar' -n 'fqdn' --source-addresses '*' --protocols 'http=80' 'https=443' --fqdn-tags "AzureKubernetesService" --action allow --priority 100
```

Mit dem folgenden Befehl können Sie dem AKS-Cluster, in dem zuvor BDC bereitgestellt wurde, eine benutzerdefinierte Routingtabelle zuordnen:

```azurecli
az network vnet subnet update -g $RESOURCE_GROUP --vnet-name $VNET_NAME --name $SUBNET_NAME --route-table $FWROUTE_TABLE_NAME
```

## <a name="create--configure-service-principal-sp"></a>Erstellen und Konfigurieren des Dienstprinzipals (Service Principal, SP)

In diesem Schritt müssen Sie den Dienstprinzipal erstellen und dem virtuellen Netzwerk eine Berechtigung zuweisen.

Sehen Sie sich folgendes Beispiel an: 

```azurecli
# Create SP and Assign Permission to Virtual Network

az ad sp create-for-rbac -n "bdcaks-sp" --skip-assignment

APPID=<your service principal ID >
PASSWORD=< your service principal password >
VNETID=$(az network vnet show -g $RESOURCE_GROUP --name $VNET_NAME --query id -o tsv)

# Assign SP Permission to VNET

az role assignment create --assignee $APPID --scope $VNETID --role "Network Contributor"


RTID=$(az network route-table show -g $RESOURCE_GROUP -n $FWROUTE_TABLE_NAME --query id -o tsv)
az role assignment create --assignee $APPID --scope $RTID --role "Network Contributor"
```

## <a name="create-aks-cluster"></a>Erstellen eines ACS-Clusters

Erstellen Sie dann den AKS-Cluster, und verwenden Sie dabei `userDefinedRouting` als ausgehenden Typ.

```azurecli
az aks create \
    --resource-group $RESOURCE_GROUP \
    --location $REGION_NAME \
    --name $AKS_NAME \
    --load-balancer-sku standard \
    --outbound-type userDefinedRouting \
    --enable-private-cluster \
    --network-plugin azure \
    --vnet-subnet-id $SUBNET_ID \
    --docker-bridge-address 172.17.0.1/16 \
    --dns-service-ip 10.2.0.10 \
    --service-cidr 10.2.0.0/24 \
    --service-principal $APPID \
    --client-secret $PASSWORD \
    --node-vm-size Standard_D13_v2 \
    --node-count 2 \
    --generate-ssh-keys
```

## <a name="build-big-data-cluster-bdc-deployment-profile"></a>Erstellen eines Bereitstellungsprofils für den Big Data-Cluster (BDC)

Sie können BDC-Cluster mit einem benutzerdefinierten Profil erstellen: 

```console
azdata bdc config init --source aks-dev-test --target private-bdc-aks --force
```

## <a name="generate-and-config-bdc-custom-deployment-profile"></a>Generieren und Konfigurieren eines benutzerdefinierten BDC-Bereitstellungsprofils: 
```console
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.docker.imageTag=2019-CU6-ubuntu-16.04"
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.storage.data.className=default"
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.storage.logs.className=default"

azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -c private-bdc-aks/control.json -j "$.spec.endpoints[1].serviceType=NodePort"

azdata bdc config replace -c private-bdc-aks/bdc.json -j "$.spec.resources.master.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -c private-bdc-aks/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].serviceType=NodePort"
azdata bdc config replace -c private-bdc-aks/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].serviceType=NodePort"
```

## <a name="deploy-bdc-in-aks-private-cluster"></a>Bereitstellen von BDC in einem privaten AKS-Cluster

```console
export AZDATA_USERNAME=<your bdcadmin username>
export AZDATA_PASSWORD=< your bdcadmin password>

azdata bdc create --config-profile private-bdc-aks --accept-eula yes
```

## <a name="use-third-party-firewall-instead-of-azure-firewall"></a>Verwenden einer Drittanbieterfirewall anstelle von Azure Firewall

Verwenden Sie eine Drittanbieterfirewall, um den ausgehenden Datenverkehr einzuschränken, wenn die Bereitstellung von BDC in einem privaten AKS-Cluster erfolgt ist. Beispiele für Firewalls finden Sie unter [Azure Marketplace: Firewalls](https://azuremarketplace.microsoft.com/marketplace/apps?search=firewall&page=1). Firewalls von Drittanbietern können in privaten Bereitstellungslösungen mit kompatibleren Konfigurationen verwendet werden. Die Firewall sollte die folgenden Netzwerkregeln unterstützen:

* Alle [erforderlichen Netzwerkregeln für ausgehenden Datenverkehr und FQDNs für AKS-Cluster](/azure/aks/limit-egress-traffic#required-outbound-network-rules-and-fqdns-for-aks-clusters) und alle HTTP-/HTTPS-Platzhalterendpunkte und alle entsprechenden Abhängigkeiten, die je nach AKS-Cluster basierend auf einer Reihe von Qualifizierern und den tatsächlichen Anforderungen variieren können.
* Die [hier](/azure/aks/limit-egress-traffic#azure-global-required-network-rules) aufgeführten für Azure Global erforderlichen Netzwerkregeln/FQDNs/Anwendungsregeln.
* Die [hier](/azure/aks/limit-egress-traffic#optional-recommended-fqdn--application-rules-for-aks-clusters) aufgeführten optionalen, empfohlenen FQDNs/Anwendungsregeln für AKS-Cluster. 

Lesen Sie [Verwalten von BDC in einem privaten AKS-Cluster](private-manage.md). Der nächste Schritt ist dann das [Herstellen einer Verbindung mit dem BDC-Cluster](connect-to-big-data-cluster.md).

Die Automatisierungsskripts für dieses Szenario finden Sie im [Repository für SQL Server-Beispiele auf GitHub](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/private-aks).

## <a name="next-steps"></a>Nächste Schritte

[Verwalten von Big Data-Clustern in einem privaten AKS-Cluster](private-manage.md)

[Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server mit Azure Data Studio](connect-to-big-data-cluster.md)
