---
title: Häufige Fehler bei Transparent Data Encryption (TDE) mit vom Kunden verwalteten Schlüsseln in Azure Key Vault | Microsoft-Dokumentation
description: Problembehandlung von Transparent Data Encryption (TDE) einer mit Azure Key Vault-Konfiguration.
helpviewer_keywords:
- troublshooting, tde akv
- tde akv configuration, troubleshooting
- tde troubleshooting
author: aliceku
manager: craigg
ms.prod: sql
ms.technology: security
ms.reviewer: vanto
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f963e15d674115029fce78b98ba280fe75da2cd1
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716668"
---
# <a name="common-errors-for-transparent-data-encryption-with-customer-managed-keys-in-azure-key-vault"></a>Häufige Fehler bei Transparent Data Encryption (TDE) mit vom Kunden verwalteten Schlüsseln in Azure Key Vault

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
Dieser Artikel beschreibt die Anforderungen für die Verwendung von Transparent Data Encryption (TDE) mit vom Kunden verwalteten Schlüsseln in Azure Key Vault und zeigt, wie häufige Fehler identifiziert und behoben werden können.

## <a name="requirements"></a>Anforderungen

Um die Problembehandlung von TDE mit einem vom Kunden verwalteten TDE-Schutz in Key Vault durchzuführen, müssen die folgenden Anforderungen erfüllt sein:

- Die logische SQL Server-Instanz und der Schlüsseltresor müssen sich in der gleichen Region befinden.
- Die Identität der logischen SQL Server-Instanz, die von Azure Active Directory (Azure AD) bereitgestellt wird (die AppId in Azure Key Vault), muss ein Mandant im ursprünglichen Abonnement sein. Wenn der Server in ein anderes Abonnement verschoben wurde, in dem er nicht erstellt wurde, muss die Serveridentität (die AppId) erneut erstellt werden.
- Der Schlüsseltresor muss aktiv sein und ausgeführt werden. Weitere Informationen zum Überprüfen des Status des Schlüsseltresors finden Sie unter [Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview). Um sich für Benachrichtigungen zu registrieren, lesen Sie mehr über [ Aktionsgruppen](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups).
- Im georedundanten Notfallwiederherstellungsszenario müssen beide Schlüsseltresore dasselbe Schlüsselmaterial enthalten, damit ein Failover funktioniert.
- Der logische Server muss über eine Azure AD-Identität (eine AppId) verfügen, um die Authentifizierung beim Schlüsseltresor auszuführen.
- Die AppId muss Zugriff auf den Schlüsseltresor besitzen, und sie muss über die Berechtigungen Get, Wrap und Unwrap für die Schlüssel verfügen, die als TDE-Schutz ausgewählt wurden.

Weitere Informationen finden Sie unter [Richtlinien zum Konfigurieren von TDE mit Azure Key Vault](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault).

## <a name="common-misconfigurations"></a>Häufige Konfigurationsfehler

Die meisten Probleme, die auftreten, wenn Sie TDE mit Key Vault verwenden, werden durch einen der folgenden Konfigurationsfehler verursacht:

### <a name="the-key-vault-is-unavailable-or-doesnt-exist"></a>Der Schlüsseltresor ist nicht verfügbar oder nicht vorhanden.

- Der Schlüsseltresor wurde versehentlich gelöscht.
- Die Firewall wurde für Azure Key Vault konfiguriert, ohne den Zugriff auf Microsoft-Dienste zuzulassen.

### <a name="no-permissions-to-access-the-key-vault-or-the-key-doesnt-exist"></a>Es liegen keine Berechtigungen für den Zugriff auf den Schlüsseltresor vor, oder der Schlüssel ist nicht vorhanden.

- Der Schlüssel wurde versehentlich gelöscht.
- Der AppId der logischen SQL Server-Instanz wurde versehentlich gelöscht.
- Die logische SQL Server-Instanz wurde in ein anderes Abonnement verschoben. Es muss eine neue AppId erstellt werden, wenn der logische Server in ein anderes Abonnement verschoben wird.
- Die der AppId für die Schlüssel erteilten Berechtigungen sind nicht ausreichend (sie beinhalten nicht Get, Wrap und Unwrap).
- Die Berechtigungen für die AppId der logischen SQL Server-Instanz wurden widerrufen.

## <a name="identify-and-resolve-common-errors"></a>Identifizieren und Beheben von häufigen Fehlern

Im diesem Abschnitt werden die Schritte zur Problembehandlung für die häufigsten Fehler aufgelistet.

### <a name="missing-server-identity"></a>Serveridentität fehlt

**Fehlermeldung**

_401 AzureKeyVaultNoServerIdentity: Die Serveridentität ist auf dem Server nicht korrekt konfiguriert. Wenden Sie sich an den Support._

**Erkennung**

Verwenden Sie das folgende Cmdlet oder den folgenden Befehl, um sicherzustellen, dass der logischen SQL Server-Instanz eine Identität zugewiesen wurde:

- Azure PowerShell: [Get-AzureRMSqlServer](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 

- Azure CLI: [az-sql-server-show](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

**Abhilfe**

Verwenden Sie das folgende Cmdlet oder den folgenden Befehl, um eine Azure AD-Identität (eine AppId) für die logische SQL Server-Instanz zu konfigurieren:

- Azure PowerShell: [Set-AzureRmSqlServer](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0) mit der Option `-AssignIdentity`.

- Azure CLI: [az sql server update](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update) mit der Option `--assign_identity`.

Navigieren Sie im Azure-Portal zum Schlüsseltresor und anschließend zu **Zugriffsrichtlinien**. Führen Sie die folgenden Schritte aus: 

 1. Verwenden Sie die Schaltfläche **Neues Element hinzufügen**, um die im vorherigen Schritt erstellte AppId für den Server hinzuzufügen. 
 1. Weisen Sie die folgenden Schlüsselberechtigungen zu: „Get (Abrufen)“, „Wrap (Packen)“ und „Unwrap (Entpacken)“. 

Weitere Informationen finden Sie unter [Zuweisen einer Azure AD-Identität zu einem Server](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server).

> [!IMPORTANT]
> Wurde die logische SQL Server-Instanz nach der TDE-Erstkonfiguration mit Key Vault in ein neues Abonnement verschoben, wiederholen Sie den Schritt zum Konfigurieren der Azure AD-Identität, um eine neue AppId zu erstellen. Fügen Sie die AppId dann dem Schlüsseltresor hinzu, und weisen Sie dem Schlüssel die richtigen Berechtigungen zu. 
>

### <a name="missing-key-vault"></a>Schlüsseltresor fehlt

**Fehlermeldung**

_503 AzureKeyVaultConnectionFailed: Der Vorgang konnte auf dem Server nicht ausgeführt werden, weil beim Versuch der Verbindungsherstellung mit Azure Key Vault Fehler aufgetreten sind._

**Erkennung**

So ermitteln Sie den Schlüssel-URI und den Schlüsseltresor:

1. Verwenden Sie das folgende Cmdlet oder den folgenden Befehl, um den Schlüssel-URI einer bestimmten logischen SQL Server-Instanz abzurufen:

    - Azure PowerShell: [Get-AzureRmSqlServerKeyVaultKey](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

    - Azure CLI: [az-sql-server-tde-key-show](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

1. Verwenden Sie den Schlüssel-URI, um den Schlüsseltresor zu identifizieren.

    - Azure PowerShell: Sie können die Eigenschaften von $MyServerKeyVaultKey untersuchen, um die Details zum Schlüsseltresor abzurufen.

    - Azure CLI: Untersuchen Sie den zurückgegebenen Serververschlüsselungsschutz, um die Details zum Schlüsseltresor abzurufen.

**Abhilfe**

Vergewissern Sie sich, dass der Schlüsseltresor verfügbar ist.

- Stellen Sie sicher, dass der Schlüsseltresor verfügbar ist und die logische SQL Server-Instanz darauf zugreifen kann.
- Befindet sich der Schlüsseltresor hinter einer Firewall, stellen Sie sicher, dass das Kontrollkästchen aktiviert ist, mit dem Microsoft-Diensten der Zugriff auf den Schlüsseltresor erlaubt wird.
- Wurde der Schlüsseltresor versehentlich gelöscht, muss die vollständige Konfiguration erneut ausgeführt werden.


### <a name="missing-key"></a>Schlüssel fehlt

**Fehlermeldungen**

_404 ServerKeyNotFound: Der angeforderte Serverschlüssel wurde im aktuellen Abonnement nicht gefunden._ 

_409 ServerKeyDoesNotExists: Der Serverschlüssel ist nicht vorhanden._

**Erkennung**

So ermitteln Sie den Schlüssel-URI und den Schlüsseltresor:

- Verwenden Sie das Cmdlet oder die Befehle unter [Schlüsseltresor fehlt](#missing-key-vault), um den Schlüssel-URI zu identifizieren, der der logischen SQL Server-Instanz hinzugefügt wird. Die Ausführung der Befehle gibt die Liste der Schlüssel zurück.

**Abhilfe**

Bestätigen Sie, dass der TDE-Schutz in Key Vault vorhanden ist:

1. Identifizieren Sie den Schlüsseltresor, und navigieren Sie dann im Azure-Portal zum Schlüsseltresor.
1. Stellen Sie sicher, dass der durch den Schlüssel-URI identifizierte Schlüssel vorhanden ist.

### <a name="missing-permissions"></a>Berechtigungen fehlen

**Fehlermeldung**

_401 AzureKeyVaultMissingPermissions: Erforderliche Serverberechtigungen für Azure Key Vault fehlen._

**Erkennung**

So identifizieren Sie den Schlüssel-URI und den Schlüsseltresor: 

- Verwenden Sie das Cmdlet oder die Befehle unter [Schlüsseltresor fehlt](#missing-key-vault), um den Schlüsseltresor zu identifizieren, den die logische SQL Server-Instanz verwendet.

**Abhilfe**

Vergewissern Sie sich, dass die logische SQL Server-Instanz über Berechtigungen für den Schlüsseltresor und über die richtigen Zugriffsberechtigungen für den Schlüssel verfügt:

- Navigieren Sie im Azure-Portal zum Schlüsseltresor und dann zu **Zugriffsrichtlinien**. Suchen Sie nach der AppId der logischen SQL Server-Instanz.  
- Ist die AppId vorhanden, vergewissern Sie sich, dass sie über die folgenden Schlüsselberechtigungen verfügt: „Get (Abrufen)“, „Wrap (Packen)“ und „Unwrap (Entpacken)“.
- Fehlt die AppId, fügen Sie sie über die Schaltfläche **Neues Element hinzufügen** hinzu. 

## <a name="next-steps"></a>Nächste Schritte

- Lesen Sie die [Richtlinien zum Konfigurieren von TDE mit Azure Key Vault](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault).
- Erfahren Sie mehr über [Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview).
- Frischen Sie Ihre Kenntnisse zum [Zuweisen einer Azure AD-Identität zu einem Server](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server) auf.
