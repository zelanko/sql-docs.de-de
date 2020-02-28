---
title: Bereitstellen im Active Directory-Modus
titleSuffix: SQL Server Big Data Cluster
description: Erfahren Sie, wie Sie für einen SQL Server-Big Data-Cluster in einer Active Directory-Domäne ein Upgrade durchführen.
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 02/13/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bd8e571417e7b2171dc135e986fa77f1f0eff089
ms.sourcegitcommit: 10ab8d797a51926e92aec977422b1ee87b46286d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544876"
---
# <a name="deploy-big-data-clusters-2019-in-active-directory-mode"></a>Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] im Active Directory-Modus

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Dokument beschrieben, wie ein SQL Server 2019-Big Data-Cluster (BDC) im Active Directory-Authentifizierungsmodus bereitgestellt wird, der eine vorhandene AD-Domäne für die Authentifizierung verwendet.

## <a name="background"></a>Hintergrund

Um die Active Directory-Authentifizierung (AD) zu aktivieren, erstellt der BDC automatisch alle Benutzer-, Gruppen- und Computerkonten sowie Dienstprinzipalnamen, die von den verschiedenen Diensten im Cluster benötigt werden. Legen Sie während der Bereitstellung eine Organisationseinheit (OE) fest, in der alle BDC-bezogenen AD-Objekte erstellt werden, um eine gewisse Begrenzung dieser Konten sowie bereichsbezogene Berechtigungen zu ermöglichen. Erstellen Sie diese Organisationseinheit vor der Clusterbereitstellung.

Um alle benötigten Objekte in Active Directory erstellen zu können, benötigt der BDC während der Bereitstellung ein AD-Konto. Dieses Konto muss über Berechtigungen zum Erstellen von Benutzern-, Gruppen- und Computerkonten innerhalb der angegebenen OE verfügen.

In den folgenden Schritten wird vorausgesetzt, dass Sie bereits über einen Active Directory-Domänencontroller verfügen. Wenn Sie noch keinen Domänencontroller eingerichtet haben, finden Sie in dieser [Anleitung](https://social.technet.microsoft.com/wiki/contents/articles/37528.create-and-configure-active-directory-domain-controller-in-azure-windows-server.aspx) nützliche Schritte.

## <a name="create-ad-objects"></a>Erstellen von AD-Objekten

Führen Sie die folgenden Schritte aus, bevor Sie einen BDC mit AD-Integration bereitstellen:

1. Erstellen Sie eine Organisationseinheit (OE), in der alle AD-Objekte für den BDC gespeichert werden. Sie können auch während der Bereitstellung eine vorhandene OE festlegen.
1. Erstellen Sie ein AD-Konto für den BDC, oder verwenden Sie ein vorhandenes Konto, und weisen Sie diesem BDC-AD-Konto die geeigneten Berechtigungen zu.

### <a name="create-a-user-in-ad-for-bdc-domain-service-account"></a>Erstellen eines Benutzers in AD für das BDC-Domänendienstkonto

Der Big Data-Cluster benötigt ein Konto mit bestimmten Berechtigungen. Bevor Sie fortfahren, müssen Sie entweder über ein vorhandenes AD-Konto verfügen oder ein neues AD-Konto erstellen, das der Big Data-Cluster zum Einrichten der erforderlichen Objekte verwenden kann.

Um in AD einen neuen Benutzer zu erstellen, können Sie mit der rechten Maustaste auf die Domäne oder die OE klicken und **Neu** > **Benutzer** auswählen:

![image12](./media/deploy-active-directory/image12.png)

Dieses Benutzerkonto wird im vorliegenden Artikel als *BDC-Domänendienstkonto* bezeichnet.

### <a name="creating-an-ou"></a>Erstellen einer Organisationseinheit

Öffnen Sie auf dem Domänencontroller **Active Directory-Benutzer und -Computer**. Klicken Sie im linken Bereich mit der rechten Maustaste auf das Verzeichnis, in dem Sie Ihre OE erstellen möchten, klicken Sie dann auf „Neu \> **Organisationseinheit**“, und folgen Sie den Anweisungen des Assistenten, um die OE zu erstellen. Alternativ können Sie eine OE mithilfe von PowerShell erstellen:

```powershell
New-ADOrganizationalUnit -Name "<name>" -Path "<Distinguished name of the directory you wish to create the OU in>"
```

In den Beispielen in diesem Artikel erhält die OE den Namen `bdc`.

![image13](./media/deploy-active-directory/image13.png)

![image14](./media/deploy-active-directory/image14.png)

### <a name="setting-permissions-the-bdc-ad-account"></a>Festlegen von Berechtigungen für das BDC-AD-Konto

Unabhängig davon, ob Sie einen neuen AD-Benutzer erstellt haben oder einen vorhandenen AD-Benutzer verwenden, benötigt der Benutzer bestimmte Berechtigungen. Dieses Konto ist das Benutzerkonto, das der BDC-Controller verwendet, um den Cluster zu AD hinzuzufügen.

Das BDC-Domänendienstkonto muss in der Lage sein, Benutzer-, Gruppen- und Computerkonten in der OE zu erstellen. In den folgenden Schritten wurde das BDC-Domänendienstkonto als `bdcDSA` benannt. Sie können einen beliebigen Namen für dieses Konto auswählen.

1. Öffnen Sie auf dem Domänencontroller **Active Directory-Benutzer und -Computer**.

1. Navigieren Sie im linken Bereich zu Ihrer Domäne und dann zu der OE, die für `bdc` verwendet wird.

1. Klicken Sie mit der rechten Maustaste auf die OE, und wählen Sie **Eigenschaften** aus.

1. Wechseln Sie zur Registerkarte „Sicherheit“. Stellen Sie hierbei sicher, dass die Einstellung **Erweiterte Funktionen** aktiviert wurde, indem Sie mit der rechten Maustaste auf die OE klicken und dann **Anzeigen** auswählen.

    ![image15](./media/deploy-active-directory/image15.png)

1. Klicken Sie auf **Hinzufügen...** , und fügen Sie den Benutzer **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]bdcDSA** hinzu.

    ![image16](./media/deploy-active-directory/image16.png)

    ![image17](./media/deploy-active-directory/image17.png)

1. Wählen Sie den Benutzer **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]bdcDSA** aus, und deaktivieren Sie alle Berechtigungen. Klicken Sie anschließend auf **Erweitert**.

1. Klicken Sie auf **Hinzufügen**.

    ![image18](./media/deploy-active-directory/image18.png)

    - Klicken Sie auf **Prinzipal auswählen**, fügen Sie **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]bdcDSA** ein, und klicken Sie auf „OK“.

    - Legen Sie den **Typ** auf **Zulassen** fest.

    - Legen Sie **Anwenden auf** auf **Dieses und alle untergeordneten Objekte** fest.

        ![image19](./media/deploy-active-directory/image19.png)

    - Scrollen Sie bis ganz nach unten, und klicken Sie auf **Alle deaktivieren**.

    - Scrollen Sie zurück nach oben, und aktivieren Sie die folgenden Berechtigungen:
       - **Alle Eigenschaften lesen**
       - **Alle Eigenschaften schreiben**
       - **Computerobjekte erstellen**
       - **Computerobjekte löschen**
       - **Gruppenobjekte erstellen**
       - **Gruppenobjekte löschen**
       - **Benutzerobjekte erstellen**
       - **Benutzerobjekte löschen**

    - Klicken Sie auf **OK**

- Klicken Sie auf **Hinzufügen**.

    - Klicken Sie auf **Prinzipal auswählen**, fügen Sie **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]bdcDSA** ein, und klicken Sie auf „OK“.

    - Legen Sie den **Typ** auf **Zulassen** fest.

    - Legen Sie **Anwenden auf** auf **Untergeordnete Computerobjekte** fest.

    - Scrollen Sie bis ganz nach unten, und klicken Sie auf **Alle deaktivieren**.

    - Scrollen Sie zurück nach oben, und wählen Sie **Kennwort zurücksetzen** aus.

    - Klicken Sie auf **OK**

- Klicken Sie auf **Hinzufügen**.

    - Klicken Sie auf **Prinzipal auswählen**, fügen Sie **[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]bdcDSA** ein, und klicken Sie auf „OK“.

    - Legen Sie den **Typ** auf **Zulassen** fest.

    - Legen Sie **Anwenden auf** auf **Untergeordnete Benutzerobjekte** fest.

    - Scrollen Sie bis ganz nach unten, und klicken Sie auf **Alle deaktivieren**.

    - Scrollen Sie zurück nach oben, und wählen Sie **Kennwort zurücksetzen** aus.

    - Klicken Sie auf **OK**

- Klicken Sie zweimal auf **OK**, um die offenen Dialogfelder zu schließen.

## <a name="prepare-deployment"></a>Vorbereiten der Bereitstellung

Um einen BDC mit AD-Integration bereitzustellen, müssen einige zusätzliche Informationen zum Erstellen der BDC-bezogenen Objekte in AD angegeben werden.

Durch Verwendung des Profils `kubeadm-prod` verfügen Sie automatisch über Platzhalter für die sicherheits- und endpunktbezogenen Informationen, die für die AD-Integration benötigt werden.

Darüber hinaus müssen Sie Anmeldeinformationen angeben, die [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] zum Erstellen der erforderlichen Objekte in AD verwendet. Diese Anmeldeinformationen werden als Umgebungsvariablen angegeben.

## <a name="set-security-environment-variables"></a>Festlegen von sicherheitsbezogenen Umgebungsvariablen

Mit den folgenden Umgebungsvariablen werden die Anmeldeinformationen für das BDC-Domänendienstkonto angegeben, das zum Einrichten der AD-Integration verwendet wird. Dieses Konto wird vom BDC außerdem dazu verwendet, die BDC-bezogenen AD-Objekte im weiteren Verlauf zu verwalten.

```bash
export DOMAIN_SERVICE_ACCOUNT_USERNAME=<AD principal account name>
export DOMAIN_SERVICE_ACCOUNT_PASSWORD=<AD principal password>
```

## <a name="provide-security-and-endpoint-parameters"></a>Angeben von Sicherheits- und Endpunktparametern

Zusätzlich zu den Umgebungsvariablen für die Anmeldeinformationen müssen Sie Sicherheits- und Endpunktinformationen angeben, damit die AD-Integration funktioniert. Die erforderlichen Parameter sind im `kubeadm-prod`-[Bereitstellungsprofil](deployment-guidance.md#configfile) bereits enthalten.

Für die AD-Integration sind die folgenden Parameter erforderlich. Fügen Sie diese Parameter zu den Dateien `control.json` und `bdc.json` hinzu, indem Sie die später in diesem Artikel beschriebenen `config replace`-Befehle verwenden. In allen nachstehenden Beispielen wird die Domäne `contoso.local` verwendet.

- `security.activeDirectory.ouDistinguishedName`: DN (Distinguished Name) einer Organisationseinheit (OE), in der alle während der Clusterbereitstellung erstellten AD-Konten gespeichert werden. Wenn die Domäne den Namen `contoso.local` aufweist, lautet der DN der Organisationseinheit `OU=BDC,DC=contoso,DC=local`.

- `security.activeDirectory.dnsIpAddresses`: Liste der IP-Adressen der Domänencontroller.

- `security.activeDirectory.domainControllerFullyQualifiedDns`: Liste der FQDNs der Domänencontroller. Der FQDN enthält den Computer-/Hostnamen eines Domänencontrollers. Wenn Sie über mehrere Domänencontroller verfügen, können Sie hier eine Liste angeben. Beispiel: `HOSTNAME.CONTOSO.LOCAL`

- **Optionaler Parameter** `security.activeDirectory.realm`: In den meisten Fällen entspricht der Bereich dem Domänennamen. Falls sich Bereich und Domänenname unterscheiden, verwenden Sie diesen Parameter zum Definieren des Bereichs (z. B. `CONTOSO.LOCAL`).

- `security.activeDirectory.domainDnsName`: Name Ihrer Domäne (z. B. `contoso.local`).

- `security.activeDirectory.clusterAdmins`: Dieser Parameter akzeptiert **eine AD-Gruppe**. Mitglieder dieser Gruppe erhalten Administratorberechtigungen im Cluster. Das bedeutet, dass Mitglieder sysadmin-Berechtigungen in SQL Server, superuser-Berechtigungen in HDFS und Administratorberechtigungen im Controller erhalten. **Beachten Sie, dass diese Gruppe in AD vorhanden sein muss, bevor die Bereitstellung beginnt. Beachten Sie auch, dass diese Gruppe nicht in Active Directory auf DomainLocal begrenzt werden kann. Eine auf DomainLocal begrenzte Gruppe führt zu einem Bereitstellungsfehler.**

- `security.activeDirectory.clusterUsers`: Liste der AD-Gruppen, die als reguläre Benutzer (ohne Administratorberechtigungen) im Big Data-Cluster fungieren. **Beachten Sie, dass diese Gruppen in AD vorhanden sein müssen, bevor die Bereitstellung beginnt. Beachten Sie auch, dass diese Gruppen nicht in Active Directory auf DomainLocal begrenzt werden können. Eine auf DomainLocal begrenzte Gruppe führt zu einem Bereitstellungsfehler.**

- **Optionaler Parameter** `security.activeDirectory.appOwners`: Liste der AD-Gruppen, die über Berechtigungen zum Erstellen, Löschen und Ausführen beliebiger Anwendungen verfügen. **Beachten Sie, dass diese Gruppen in AD vorhanden sein müssen, bevor die Bereitstellung beginnt. Beachten Sie auch, dass diese Gruppen nicht in Active Directory auf DomainLocal begrenzt werden können. Eine auf DomainLocal begrenzte Gruppe führt zu einem Bereitstellungsfehler.**

- **Optionaler Parameter** `security.activeDirectory.appReaders`: Dieser Parameter ist eine Liste der AD-Gruppen, die über Berechtigungen zum Ausführen einer beliebigen Anwendung verfügen. **Beachten Sie, dass diese Gruppen in AD vorhanden sein müssen, bevor die Bereitstellung beginnt. Beachten Sie auch, dass diese Gruppen nicht in Active Directory auf DomainLocal begrenzt werden können. Eine auf DomainLocal begrenzte Gruppe führt zu einem Bereitstellungsfehler.**

**Überprüfen des AD-Gruppenbereichs:** 
 Anweisungen zum Überprüfen des Bereichs einer AD-Gruppe, um zu ermitteln, ob sie auf DomainLocal begrenzt ist, finden Sie [hier](https://docs.microsoft.com/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps).

Wenn Sie Konfigurationsdatei für die Bereitstellung noch nicht initialisiert haben, können Sie diesen Befehl ausführen, um eine Kopie der Konfiguration abzurufen.

```bash
azdata bdc config init --source kubeadm-prod  --target custom-prod-kubeadm
```

Um die oben aufgeführten Parameter in der Datei `control.json` festzulegen, verwenden Sie die folgenden `azdata`-Befehle. Über diese Befehle werden die Konfigurationswerte vor der Bereitstellung durch Ihre eigenen Werte ersetzt.

 > [!IMPORTANT]
 > Im SQL Server 2019 CU2-Release hat sich die Struktur des Sicherheitskonfigurationsabschnitts im Bereitstellungsprofil leicht geändert, sodass nun alle Einstellungen im Zusammenhang mit Active Directory im neuen *activeDirectory* in der json-Struktur unter *security* in der Datei *control.json* zu finden sind.

Im nachfolgenden Beispiel wird SQL Server 2019 CU2 verwendet. Dort wird gezeigt, wie Sie die AD-bezogenen Parameterwerte in der Bereitstellungskonfiguration ersetzen. Die Domänendetails unten sind Beispielwerte.

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.activeDirectory.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

In Releases vor SQL Server 2019 CU2 können Sie entsprechend Folgendes ausführen:

```bash
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.ouDistinguishedName=OU\=bdc\,DC\=contoso\,DC\=local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.dnsIpAddresses=[\"10.100.10.100\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainControllerFullyQualifiedDns=[\"HOSTNAME.CONTOSO.LOCAL\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.domainDnsName=contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterAdmins=[\"bdcadminsgroup\"]"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.security.clusterUsers=[\"bdcusersgroup\"]"
#Example for providing multiple clusterUser groups: [\"bdcusergroup1\",\"bdcusergroup2\"]
```

Zusätzlich zu den Informationen oben müssen Sie DNS-Namen für die verschiedenen Clusterendpunkte angeben. Die DNS-Einträge mit den angegebenen DNS-Namen werden während der Bereitstellung automatisch in Ihrem DNS-Server erstellt. Sie verwenden diese Namen, wenn Sie eine Verbindung mit den verschiedenen Clusterendpunkten herstellen. Wenn der DNS-Name für die SQL-Masterinstanz beispielsweise `mastersql` lautet, verwenden Sie `mastersql.contoso.local,31433`, um von den Tools aus eine Verbindung mit der Masterinstanz herzustellen.

> [!NOTE]
> Stellen Sie sicher, dass Sie im DNS-Server DNS-Einträge für die nachstehend definierten Namen erstellen. Für `kubeadm`-Bereitstellungen können Sie beispielsweise die IP-Adresse des Kubernetes-Hauptknotens verwenden, wenn Sie die DNS-Einträge erstellen.

```bash
# DNS names for BDC services
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[0].dnsName=<controller DNS name>.contoso.local"
azdata bdc config replace -c custom-prod-kubeadm/control.json -j "$.spec.endpoints[1].dnsName=<monitoring services DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[0].dnsName=<SQL Master Primary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.master.spec.endpoints[1].dnsName=<SQL Master Secondary DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.gateway.spec.endpoints[0].dnsName=<Gateway (Knox) DNS name>.<Domain name. e.g. contoso.local>"
azdata bdc config replace -c custom-prod-kubeadm/bdc.json -j "$.spec.resources.appproxy.spec.endpoints[0].dnsName=<app proxy DNS name>.<Domain name. e.g. contoso.local>"
```

Sie finden hier ein Beispielskript für die [ Bereitstellung eines SQL Server-Big Data-Clusters in einem Einzelknoten-Kubernetes-Cluster (kubeadm) mit AD-Integration](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm-ad).

Sie sollten jetzt alle erforderlichen Parameter für eine BDC-Bereitstellung mit Active Directory-Integration festgelegt haben.

Eine vollständige Dokumentation zur Bereitstellung von [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] finden Sie in der [offiziellen Dokumentation](deployment-guidance.md).

## <a name="verify-reverse-dns-entry-for-domain-controller"></a>Überprüfen der Reverse-DNS-Einträge für den Domänencontroller

Stellen Sie sicher, dass ein Reverse-DNS-Eintrag (PTR-Eintrag) für den Domänencontroller selbst im DNS-Server registriert ist. Sie können dies überprüfen, indem Sie `nslookup` für den Domänennamen im Domänencontroller ausführen, um sicherzustellen, dass der Name in die IP-Adresse des Domänencontrollers aufgelöst wird.

## <a name="connect-to-cluster-endpoints-in-ad-mode"></a>Verbindungsherstellung mit Clusterendpunkten im AD-Modus

Melden Sie sich über die AD-Authentifizierung bei der SQL Server-Masterinstanz an.

Um AD-Verbindungen mit der SQL Server-Instanz zu überprüfen, stellen Sie mit `sqlcmd` eine Verbindung mit der SQL-Masterinstanz her. Für die angegebenen Gruppen werden bei der Bereitstellung automatisch Anmeldungen erstellt (`clusterUsers` und `clusterAdmins`).

Wenn Sie Linux verwenden, führen Sie zunächst `kinit` als der AD-Benutzer und dann `sqlcmd` aus. Bei Verwendung von Windows melden Sie sich einfach als der gewünschte Benutzer von einem **in die Domäne eingebundenen Clientcomputer** aus an.

### <a name="connect-to-master-instance-from-linuxmac"></a>Verbindungsherstellung mit der Masterinstanz unter Linux/Mac

```bash
kinit <username>@<domain name>
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="connect-to-master-instance-from-windows"></a>Verbindungsherstellung mit der Masterinstanz unter Windows

```cmd
sqlcmd -S <DNS name for master instance>,31433 -E
```

### <a name="log-in-to-sql-server-master-instance-using-azure-data-studio-or-ssms"></a>Anmeldung bei der SQL Server-Masterinstanz über Azure Data Studio oder SSMS

Von einem in die Domäne eingebundenen Client aus können Sie SSMS oder Azure Data Studio öffnen und eine Verbindung mit der Masterinstanz erstellen. Dies entspricht der Verbindungsherstellung mit einer beliebigen SQL Server-Instanz über die AD-Authentifizierung.

Aus SSMS:

![image23](./media/deploy-active-directory/image23.png)

Aus Azure Data Studio:

![image24](./media/deploy-active-directory/image24.png)}

### <a name="log-in-to-controller-with-ad-authentication"></a>Anmeldung beim Controller mithilfe der AD-Authentifizierung

#### <a name="connect-to-controller-with-ad-authentication-from-linuxmac"></a>Verbindungsherstellung mit dem Controller mithilfe der AD-Authentifizierung unter Linux/Mac

Sie können über `azdata` und die AD-Authentifizierung eine Verbindung mit dem Controllerendpunkt herstellen.

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
```

#### <a name="connect-to-controller-with-ad-authentication-from-windows"></a>Verbindungsherstellung mit dem Controller mithilfe der AD-Authentifizierung unter Windows

```cmd
azdata login -e https://<controller DNS name>:30080 --auth ad
```

### <a name="use-ad-authentication-to-knox-gateway-webhdfs"></a>Verwenden der AD-Authentifizierung für das Knox-Gateway (webHDFS)

Sie können auch HDFS-Befehle unter Verwendung von curl über den Knox-Gatewayendpunkt ausführen. Dies erfordert eine AD-Authentifizierung bei Knox. Der nachstehende curl-Befehl löst einen webHDFS-REST-Aufruf über das Knox-Gateway auf, um ein Verzeichnis namens `products` zu erstellen.

```bash
curl -k -v --negotiate -u : https://<Gateway DNS name>:30443/gateway/default/webhdfs/v1/products?op=MKDIRS -X PUT
```

## <a name="known-issues-and-limitations"></a>Einschränkungen und bekannte Probleme

**Bekannte Einschränkungen für dieses Release:**

- Aktuell bieten das Dashboard für die Protokollsuche und das Metrikdashboard keine Unterstützung für die AD-Authentifizierung. Die AD-Unterstützung für diesen Endpunkt ist für eine zukünftige Version geplant. Zur Authentifizierung bei diesen Dashboards kann die bei der Bereitstellung angegebene Kombination aus Benutzername und Kennwort für die Standardauthentifizierung verwendet werden. Alle weiteren Clusterendpunkte unterstützen die AD-Authentifizierung.

- Der sichere AD-Modus funktioniert aktuell nur für `kubeadm`-Bereitstellungsumgebungen, nicht für AKS. Das Bereitstellungsprofil `kubeadm-prod` umfasst standardmäßig die Sicherheitsabschnitte.

- Pro Domäne ist aktuell nur ein BDC zugelassen. Die Aktivierung mehrerer BDCs pro Domäne ist für eine zukünftige Version geplant.

- Keine der AD-Gruppen, die in Sicherheitskonfigurationen angegeben werden, können auf DomainLocal begrenzt werden. Sie können den Bereich einer AD-Gruppe überprüfen, indem Sie [diese Anweisungen befolgen](https://docs.microsoft.com/powershell/module/activedirectory/get-adgroup?view=winserver2012-ps&viewFallbackFrom=winserver2012r2-ps).
