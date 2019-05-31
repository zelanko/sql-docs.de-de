---
title: Häufige Fehler und deren Lösungen für Transparent Data Encryption (TDE) mit vom Kunden verwalteten Schlüsseln im Azure Key Vault (AKV) | Microsoft-Dokumentation
description: Problembehandlung für Transparent Data Encryption (TDE) mit Azure Key Vault-Konfiguration
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
ms.openlocfilehash: e6d23fb19b756bbf303a06512fecc3a6d29b8090
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65097450"
---
# <a name="transparent-data-encryption-tde-with-customer-managed-keys-in-azure-key-vault-akv-troubleshooting"></a>Transparent Data Encryption (TDE) mit vom Kunden verwalteten Schlüsseln im Azure Key Vault (AKV) – Problembehandlung

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
In diesem Thema finden Sie Informationen zu den folgenden Punkten:  
  
- Anforderungen  
- Identifizieren und Beheben der häufigsten Fehler

## <a name="requirements"></a>Anforderungen
Lesen Sie die folgenden Anforderungen, bevor Sie mit der Problembehandlung für [TDE mit einer vom Kunden verwalteten TDE-Schutzvorrichtung mit AKV-Konfiguration](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault) beginnen:
- Der logische SQL Server und der Schlüsseltresor müssen sich in derselben Region befinden.
- Die von Azure Active Directory bereitgestellte Identität des logischen SQL Servers (APPID im Azure Key Vault) ist auf einen Mandanten im ursprünglichen Abonnement beschränkt.  Wird der Server in ein anderes Abonnement verschoben, muss die Serveridentität (APPID) neu erstellt werden.
- Der Schlüsseltresor muss einsatzbereit sein. Informationen zum Überprüfen des Key Vault-Status finden Sie unter [Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview) und zum Registrieren für Benachrichtigungen unter [Aktionsgruppen](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups).
- Im georedundanten Notfallwiederherstellungsszenario müssen beide Schlüsseltresore dasselbe Schlüsselmaterial für ein Failover enthalten.
- Der logische Server muss über eine Azure Active Directory-Identität (APPID) verfügen, um sich beim Schlüsseltresor authentifizieren zu können.
- Die APPID muss auf den Schlüsseltresor zugreifen und Berechtigungen für die als TDE-Schutzvorrichtung ausgewählten Schlüssel packen, entpacken und abrufen können.

Die meisten Probleme, die bei der Verwendung von TDE mit AKV auftreten, sind die Folge eines der folgenden Konfigurationsfehler:

### <a name="key-vault-unavailable-or-doesnt-exist"></a>Der Schlüsseltresor ist nicht verfügbar oder nicht vorhanden
- Der Schlüsseltresor wurde versehentlich gelöscht.
- Die Firewall wurde für den Azure Key Vault konfiguriert, ohne den Zugriff auf Microsoft-Dienste zuzulassen.

### <a name="no-permissions-to-access-the-key-vault-or-key-doesnt-exist"></a>Die Zugriffsberechtigungen für den Schlüsseltresor oder der Schlüssel sind nicht vorhanden
- Der Schlüssel wurde versehentlich gelöscht.
- Die APPID von SQL wurde versehentlich gelöscht.
- SQL wurde in ein anderes Abonnement verschoben, wodurch eine neue APPID erforderlich ist.
- Die der APPID gewährten Berechtigungen für Schlüssel sind nicht ausreichend (Packen, Entpacken, Abrufen).
- Die Berechtigungen für die APPID von SQL wurden widerrufen.


Im nächsten Abschnitt werden die Schritte zur Problembehandlung für die häufigsten Fehler aufgelistet.


## <a name="how-to-identify-and-resolve-the-most-common-errors"></a>Identifizieren und Beheben der häufigsten Fehler

## <a name="missing-server-identity"></a>Serveridentität fehlt
Fehlermeldung: „401 AzureKeyVaultNoServerIdentity: Die Serveridentität ist auf dem Server nicht korrekt konfiguriert. Wenden Sie sich an den Support.“

Erkennung: Verwenden Sie den folgenden Befehl, um sicherzustellen, dass dem logischen SQL Server eine Identität zugewiesen wurde:

- [Get-AzureRMSqlServer in Azure PowerShell](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 
- [az-sql-server-show in der Azure CLI](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

Abhilfe: Konfigurieren Sie eine Azure Active Directory-Identität (APPID) für den logischen SQL Server.

Mit PowerShell: Verwenden Sie den Befehl „Set-AzureRmSqlServer“ mit der Option [- AssignIdentity](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0). 

Über die CLI: Verwenden Sie den Befehl „az sql server update“ mit der Option [--assign_identity](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update). 

Navigieren Sie im Azure-Portal zum Schlüsseltresor und anschließend auf die Zugriffsrichtlinien:  
 - Verwenden Sie die Schaltfläche „Neues Element hinzufügen“, um die im vorherigen Schritt erstellte APPID für den Server hinzuzufügen. 
 - Weisen Sie die folgenden Schlüsselberechtigungen zu: „Get (Abrufen)“, „Wrap (Packen)“ und „Unwrap (Entpacken)“. 

[Weitere Informationen](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server)

> [!IMPORTANT]
> Wurde der logische SQL Server nach der TDE-Erstkonfiguration mit AKV in ein neues Abonnement verschoben, muss die AAD-Identität erneut konfiguriert werden, um eine neue APPID zu erstellen.  Die neue APPID muss anschließend dem Schlüsseltresor hinzugefügt werden, und die korrekten Berechtigungen müssen erneut zugewiesen werden. 
>

## <a name="missing-key-vault"></a>Schlüsseltresor fehlt
Fehlermeldung: „503 AzureKeyVaultConnectionFailed: Der Vorgang konnte auf dem Server nicht ausgeführt werden, weil beim Versuch der Verbindungsherstellung mit dem Azure Key Vault Fehler aufgetreten sind.“

Erkennung: Ermitteln Sie die Schlüssel-URI und den Schlüsseltresor. 

Schritt 1: Verwenden Sie den folgenden Befehl, um die Schlüssel-URI eines bestimmten logischen SQL Servers abzurufen:

-[get-azurermsqlserverkeyvaultkey in Azure PowerShell](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

-[az-sql-server-tde-key-show in der Azure CLI](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

Schritt 2: Verwenden Sie die Schlüssel-URI, um den Schlüsseltresor zu ermitteln.

Mit PowerShell: Überprüfen Sie die Eigenschaften von „$MyServerKeyVaultKey“, um die Details zum Schlüsseltresor abzurufen.

Über die CLI: Überprüfen Sie den zurückgegebenen Serververschlüsselungsschutz, um die Details zum Schlüsseltresor abzurufen.

Abhilfe: Vergewissern Sie sich, dass der Schlüsseltresor verfügbar ist.
- Stellen Sie sicher, dass der Schlüsseltresor verfügbar ist und der logische SQL Server darauf zugreifen kann.
- Befindet sich der Schlüsseltresor hinter eine Firewall, stellen Sie sicher, dass das Kontrollkästchen aktiviert ist, mit dem Microsoft-Diensten der Zugriff auf den Schlüsseltresor erlaubt wird.
- Wurde der Schlüsseltresor versehentlich gelöscht, muss die komplette Konfiguration erneut ausgeführt werden.


## <a name="missing-key"></a>Schlüssel fehlt 
Fehlermeldung: „404 ServerKeyNotFound - The requested server key was not found on the current subscription.“ (404 ServerKeyNotFound: Der angeforderte Serverschlüssel wurde im aktuellen Abonnement nicht gefunden.)
„409 ServerKeyDoesNotExists - The server key does not exist.“ (409 ServerKeyDoesNotExists: Der Serverschlüssel ist nicht vorhanden.)

Erkennung: Ermitteln Sie die Schlüssel-URI und den Schlüsseltresor.
- Ermitteln Sie mithilfe der Cmdlets aus dem Abschnitt „Schlüsseltresor fehlt“ weiter oben die Schlüssel-URI, die dem logischen SQL Server hinzugefügt wurde, um die Liste mit Schlüsseln zurückzugeben.

Abhilfe: Vergewissern Sie sich, dass die TDE-Schutzvorrichtung in AKV vorhanden ist.
- Ermitteln Sie den Schlüsseltresor, und suchen Sie ihn im Azure-Portal.
- Stellen Sie sicher, dass der durch die Schlüssel-URI identifizierte Schlüssel vorhanden ist.

## <a name="missing-permissions"></a>Berechtigungen fehlen 
Fehlermeldung: „"401 AzureKeyVaultMissingPermissions - The server is missing required permissions on the Azure Key Vault. (401 AzureKeyVaultMissingPermissions: Erforderliche Serverberechtigungen für den Azure Key Vault fehlen.)

Erkennung: Ermitteln Sie die Schlüssel-URI und den Schlüsseltresor.
- Ermitteln Sie mithilfe der Cmdlets aus dem Abschnitt „Schlüsseltresor fehlt“ weiter oben den Schlüsseltresor, der vom logischen SQL Server verwendet wird.

Abhilfe: Vergewissern Sie sich, dass der logische SQL Server über Berechtigungen für den Schlüsseltresor und über die korrekten Zugriffsberechtigungen für den Schlüssel verfügt.
- Navigieren Sie im Azure-Portal zum Schlüsseltresor, anschließend auf die Zugriffsrichtlinien, und suchen Sie nach der SQL Server-APPID:  
  - Fehlt die APPID, fügen Sie sie über die Schaltfläche „Neues Element hinzufügen“ hinzu. 
  - Ist die APPID vorhanden, vergewissern Sie sich, dass sie über die folgenden Schlüsselberechtigungen verfügt: „Get (Abrufen)“, „Wrap (Packen)“ und „Unwrap (Entpacken)“.
