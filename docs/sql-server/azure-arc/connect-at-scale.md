---
title: Herstellen einer Verbindung zwischen SQL Server-Instanzen und Azure Arc im großen Stil
titleSuffix: ''
description: In diesem Artikel erfahren Sie, wie Sie mithilfe eines Dienstprinzipals eine Verbindung für SQL Server-Instanzen als Azure Arc-fähige SQL Server-Instanzen (Vorschau) herstellen.
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 36d4581756cd89e016658f8e415aaec6fbe9a35b
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988006"
---
# <a name="connect-sql-server-instances-to-azure-arc-at-scale"></a>Herstellen einer Verbindung zwischen SQL Server-Instanzen und Azure Arc im großen Stil

Sie können das [für einen einzelnen Computer generierte Skript](connect.md) auch verwenden, um mehrere SQL Server-Instanzen, die auf verschiedenen Windows- oder Linux-Computern installiert sind, mit Azure Arc zu verbinden. Das Skript stellt für alle Computer und die darauf installierten SQL Server-Instanzen eine Verbindung mit Azure Arc her und registriert sie dort. Für optimale Ergebnisse wird die Verwendung eines Azure Active Directory-[Dienstprinzipals](/azure/active-directory/develop/app-objects-and-service-principals) empfohlen. Bei einem Dienstprinzipal handelt es sich um eine spezielle eingeschränkte Verwaltungsidentität, der nur die Mindestberechtigungen erteilt werden, die erforderlich sind, um Computer mit Azure zu verbinden und die Azure-Ressourcen für Azure Arc-fähige Server und Azure Arc-fähige SQL Server-Instanzen zu erstellen. Dies ist sicherer als die Verwendung eines Kontos mit höherer Berechtigung, wie z. B. einem Mandantenadministrator, und befolgt unsere bewährten Methoden für die Sicherheit der Zugriffssteuerung.  

Die Methoden zum Installieren und Konfigurieren des Connected Machine-Agents erfordern, dass die von Ihnen verwendete automatisierte Methode über Administratorberechtigungen auf den Computern verfügt. Unter Linux muss hierfür das root-Konto verwendet werden. Unter Windows müssen Sie Mitglied der Gruppe „Lokale Administratoren“ sein.

Bevor Sie beginnen, sollten Sie die [Voraussetzungen](overview.md#prerequisites) überprüfen und sicherstellen, dass Sie eine benutzerdefinierte Rolle erstellt haben, die über die erforderlichen Berechtigungen verfügt.

## <a name="connecting-multiple-sql-server-instances-on-windows-using-azure-powershell"></a>Herstellen einer Verbindung für mehrere SQL Server-Instanzen unter Windows mithilfe von Azure PowerShell

Auf jedem Computer muss [Azure PowerShell](/powershell/azure/install-az-ps) installiert sein.

1. Erstellen Sie den Dienstprinzipal über PowerShell mit dem Cmdlet [`New-AzADServicePrincipal`](/powershell/module/az.resources/new-azadserviceprincipal). Stellen Sie sicher, dass Sie die Ausgabe in einer Variablen speichern. Andernfalls können Sie das später benötigte Kennwort nicht abrufen.

    ```azurepowershell-interactive
    $sp = New-AzADServicePrincipal -DisplayName "Arc-for-servers" -Role <your custom role>
    $sp
    ```

    ```output
    Secret                : System.Security.SecureString
    ServicePrincipalNames : {ad9bcd79-be9c-45ab-abd8-80ca1654a7d1, https://Arc-for-servers}
    ApplicationId         : ad9bcd79-be9c-45ab-abd8-80ca1654a7d1
    ObjectType            : ServicePrincipal
    DisplayName           : Hybrid-RP
    Id                    : 5be92c87-01c4-42f5-bade-c1c10af87758
    Type                  :
    ```

   > [!NOTE]
   > Beim Erstellen eines Dienstprinzipals muss Ihr Konto Besitzer oder Benutzerzugriffsadministrator in dem Abonnement sein, das Sie für das Onboarding verwenden möchten. Falls Sie nicht über ausreichende Berechtigungen zum Erstellen von Rollenzuweisungen verfügen, wird der Dienstprinzipal zwar vielleicht erstellt, kann aber keine Computer integrieren. Die Anweisungen für das Erstellen einer benutzerdefinierten Rolle finden Sie unter [Erforderliche Berechtigungen](overview.md#required-permissions).

2. Rufen Sie das in der Variablen `$sp` gespeicherte Kennwort ab:

   ```azurepowershell-interactive
   $credential = New-Object pscredential -ArgumentList "temp", $sp.Secret
   $credential.GetNetworkCredential().password
   ```
3. Rufen Sie den Wert für die Mandanten-ID des Dienstprinzipals ab:
 
   ```azurepowershell-interactive
   $tenantId= (Get-AzContext).Tenant.Id
   ```
4. Kopieren und speichern Sie die Werte für Kennwort, Anwendungs-ID und Mandanten-ID mit entsprechenden Sicherheitsmaßnahmen. Sollten Sie Ihr Dienstprinzipalkennwort vergessen oder verlieren, können Sie es mithilfe des Cmdlets [`New-AzADSpCredential`](/powershell/module/azurerm.resources/new-azurermadspcredential) zurücksetzen.

   > [!NOTE]
   > Beachten Sie, dass Azure Arc für Server die Anmeldung mit einem Zertifikat derzeit nicht unterstützt. Daher muss der Dienstprinzipal über ein Geheimnis für die Authentifizierung verfügen.

5. Laden Sie das PowerShell-Skript wie in der Anleitung unter [Herstellen einer Verbindung zwischen Ihrer SQL Server-Instanz und Azure Arc](connect.md) beschrieben im Portal herunter.

6. Öffnen Sie das Skript in einer Administratorinstanz von PowerShell ISE, und ersetzen Sie die folgenden Umgebungsvariablen durch die bei der zuvor beschriebenen Dienstprinzipalbereitstellung generierten Werte. Diese Variablen sind anfangs leer.

   ```azurepowershell-interactive
   $servicePrincipalAppId="{serviceprincipalAppID}"
   $servicePrincipalSecret="{serviceprincipalPassword}"
   $servicePrincipalTenantId="{serviceprincipalTenantId}"
   ```

7. Führen Sie das Skript auf allen Zielcomputern aus.

## <a name="connecting-multiple-sql-server-instances-on-linux-using-azure-cli"></a>Herstellen einer Verbindung für mehrere SQL Server-Instanzen unter Linux mithilfe der Azure CLI

Auf jedem Zielcomputer muss die [Azure CLI installiert](/cli/azure/install-azure-cli) sein. Das Registrierungsskript führt automatisch eine Anmeldung bei Azure mit den Anmeldeinformationen des Dienstprinzipals durch, wenn diese bereitgestellt wurden und nicht bereits ein anderer Benutzer angemeldet ist. Führen Sie die folgenden Schritte aus, um für SQL Server-Instanzen auf mehreren Linux-Computern eine Verbindung herzustellen.

1. Erstellen Sie mit dem Befehl [az ad sp create-for-rbac](/cli/azure/ad/sp.md#az_ad_sp_create_for_rbac) den Dienstprinzipal. 

   ```azurecli-interactive
   az ad sp create-for-rbac --name <your service principal name> --role <your custom role name>    
   ```

   ```output
   { "appId": "d2ff754a-e10a-4eb6-9cdc-ce6e7a4687db",
     "displayName": "Arc-for-servers",
     "name": "http://Arc-for-servers",
     "password": {SomeRandomlyGeneratedPassword}",
     "tenant": "2530e75f-673b-4841-8270-47ca6a34ef4f"
   }
   ```

   > [!NOTE]
   > Beim Erstellen eines Dienstprinzipals muss Ihr Konto Besitzer oder Benutzerzugriffsadministrator in dem Abonnement sein, das Sie für das Onboarding verwenden möchten. Falls Sie nicht über ausreichende Berechtigungen zum Erstellen von Rollenzuweisungen verfügen, wird der Dienstprinzipal zwar vielleicht erstellt, kann aber keine Computer integrieren. Die Anweisungen für das Erstellen einer benutzerdefinierten Rolle finden Sie unter [Erforderliche Berechtigungen](overview.md#required-permissions).

2. Laden Sie das Linux-Shellskript wie in der Anleitung unter [Herstellen einer Verbindung zwischen Ihrer SQL Server-Instanz und Azure Arc](connect.md) beschrieben im Portal herunter.

3. Ersetzen Sie die folgenden Variablen im Skript durch die für den Befehl „az ad sp create-for-rbac“ zurückgegebenen Werte. Diese Variablen sind anfangs leer.

   ```bash
   servicePrincipalAppId="{serviceprincipalAppID}"
   servicePrincipalSecret="{serviceprincipalPassword}"
   servicePrincipalTenant="{serviceprincipalTenant}"
   ```

3. Führen Sie das Skript auf allen Zielcomputern aus.
 
   ```bash
   sudo chmod +x ./RegisterSqlServerArc.sh
   ./RegisterSqlServerArc.sh
   ```

## <a name="validate-successful-onboarding"></a>Überprüfen des erfolgreichen Onboardings

Navigieren Sie nach dem Registrieren der SQL Server-Instanzen mit Azure Arc-fähigen SQL Server-Instanzen (Vorschau) zum [Azure-Portal](https://aka.ms/azureportal), und zeigen Sie die neu erstellten Azure Arc-Ressourcen an. Für jeden verbundenen Computer wird eine neue Ressource vom Typ __Computer – Azure Arc__ angezeigt und für jede registrierte SQL Server-Instanz eine neue Ressource vom Typ __SQL Server – Azure Arc__. 

![Erfolgreiches Onboarding](./media/join-at-scale/successful-onboard.png)

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie, wie Sie Ihren Computer mithilfe von [Azure Policy](/azure/governance/policy/overview) verwalten, wie z. B. bei der VM-[Gastkonfiguration](/azure/governance/policy/concepts/guest-configuration), dem Überprüfen, ob der Computer dem erwarteten Log Analytics-Arbeitsbereich Bericht erstattet, beim Aktivieren der Überwachung mit [Azure Monitor mit VMs](/azure/azure-monitor/insights/vminsights-enable-policy) und vieles mehr.

- Weitere Informationen zum [Log Analytics-Agent](/azure/azure-monitor/platform/log-analytics-agent). Der Log Analytics-Agent für Windows und Linux ist erforderlich, wenn Sie das Betriebssystem und die Workloads auf dem Computer proaktiv überwachen, den Computer mithilfe von Automation-Runbooks oder Lösungen wie der Updateverwaltung verwalten oder andere Azure-Dienste wie [Azure Security Center](/azure/security-center/security-center-intro) verwenden möchten.

- Informieren Sie sich darüber, [wie Sie Ihre SQL Server-Instanz für eine regelmäßige Umgebungsintegritätsprüfung mithilfe der bedarfsgesteuerten SQL-Bewertung konfigurieren](assess.md).

- Informieren Sie sich darüber, wie Sie [erweiterte Datensicherheit für Ihre SQL Server-Instanz konfigurieren](configure-advanced-data-security.md).