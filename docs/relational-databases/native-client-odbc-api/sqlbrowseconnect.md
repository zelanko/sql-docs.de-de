---
title: Sqlbrowseconnetct | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 690e853ceb908cb85d27831c0c9a4961591158f8
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012089"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **Sqlbrowseconnetct** verwendet Schlüsselwörter, die in drei Ebenen von Verbindungsinformationen kategorisiert werden können. In der folgenden Tabelle wird für jedes Schlüsselwort angegeben, ob eine Liste gültiger Werte zurückgegeben wird und ob das Schlüsselwort optional ist.  
  
## <a name="level-1"></a>Ebene 1  
  
|Stichwort|Liste zurückgegeben?|Optional?|BESCHREIBUNG|  
|-------------|--------------------|---------------|-----------------|  
|DSN|–|Nein|Der Name der von **SQLDataSources**zurückgegebenen Datenquelle. Das DSN-Schlüsselwort kann nicht verwendet werden, wenn das DRIVER-Schlüsselwort verwendet wird.|  
|DRIVER|–|Nein|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Name des ODBC-Treibers für Microsoft® Native Client lautet { [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11}. Das DRIVER-Schlüsselwort kann nicht verwendet werden, wenn das DSN-Schlüsselwort verwendet wird.|  
  
## <a name="level-2"></a>Ebene 2  
  
|Stichwort|Liste zurückgegeben?|Optional?|BESCHREIBUNG|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Ja|Nein |Name des Servers in dem Netzwerk, auf dem die Datenquelle gespeichert ist. Für den Server kann der Begriff "(local)" eingegeben werden. In diesem Fall kann eine lokale Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden, auch wenn dies keine vernetzte Version ist.|  
|UID|Nein|Ja|Benutzeranmelde-ID.|  
|PWD|Nein|Ja (vom Benutzer abhängig)|Vom Benutzer angegebenes Kennwort.|  
|APP|Nein|Ja|Der Name der Anwendung, die **sqlbrowseconnetct**aufrufen.|  
|WSID|Nein|Ja|Workstation-ID. Dies ist normalerweise der Netzwerkname des Computers, auf dem die Anwendung ausgeführt wird.|  
  
## <a name="level-3"></a>Level 3  
  
|Stichwort|Liste zurückgegeben?|Optional?|BESCHREIBUNG|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Ja|Ja|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|LANGUAGE|Ja|Ja|Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendete Landessprache.|  
  
 **Sqlbrowseconnetct** ignoriert die Werte der in den ODBC-Datenquellen Definitionen gespeicherten Datenbank-und sprach Schlüsselwörter. Wenn die in der Verbindungs Zeichenfolge, die an **sqlbrowseconnetct** weitergegeben wurde, angegebene Datenbank oder Sprache ungültig ist, gibt **sqlbrowseconnetct** SQL_NEED_DATA und die Verbindungs Attribute der Ebene 3 zurück.  
  
 Die folgenden Attribute, die durch den Aufruf von [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)festgelegt werden, bestimmen das von **sqlbrowseconnetct**zurückgegebene Resultset.  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Wenn Sie auf SQL_MORE_INFO_YES festgelegt ist, gibt **sqlbrowseconnetct** eine erweiterte Zeichenfolge mit Server Eigenschaften zurück.<br /><br /> Im folgenden finden Sie ein Beispiel für eine erweiterte Zeichenfolge, die von **sqlbrowseconnetct**zurückgegeben wird:<br /><br /> <br /><br /> `ServerName\InstanceName;Clustered:No;Version:8.00.131`<br /><br /> <br /><br /> In dieser Zeichenfolge werden verschiedene durch Semikolons getrennte Informationen zum Server aufgeführt. Informationen zu verschiedenen Serverinstanzen werden durch Kommas getrennt.|  
|SQL_COPT_SS_BROWSE_SERVER|Wenn ein Servername angegeben wird, gibt **sqlbrowseconnetct** Informationen für den angegebenen Server zurück. Wenn SQL_COPT_SS_BROWSE_SERVER auf NULL festgelegt ist, gibt **sqlbrowseconnetct** Informationen für alle Server in der Domäne zurück.<br /><br /> <br /><br /> Beachten Sie, dass **sqlbrowseconnetct** aufgrund von Netzwerkproblemen möglicherweise keine rechtzeitige Antwort von allen Servern empfängt. Daher kann die Liste der zurückgegebenen Server bei jeder Anforderung unterschiedlich sein.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Wenn die Pufferlänge nicht groß genug ist, um das Ergebnis aufzunehmen, können Sie das Attribut SQL_COPT_SS_BROWSE_CACHE_DATA auf SQL_CACHE_DATA_YES festlegen und Daten in Abschnitten abrufen. Diese Länge wird im BufferLength-Argument für sqlbrowseconnetct angegeben.<br /><br /> Wenn weitere Daten verfügbar sind, wird SQL_NEED_DATA zurückgegeben. Wenn keine weiteren Daten abrufbar sind, wird SQL_SUCCESS zurückgegeben.<br /><br /> Der Standardwert ist SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>SQLBrowseConnect-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall  
 Weitere Informationen zur Verwendung von **sqlbrowseconnetct** für die Verbindung mit einem- [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] Cluster finden Sie [unter SQL Server Native Client-Unterstützung für hohe Verfügbarkeit und Notfall Wiederherstellung](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>SQLBrowseConnect-Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPNs)  
 Wenn eine Verbindung hergestellt wird, legt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client für SQL_COPT_SS_MUTUALLY_AUTHENTICATED und SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD die für das Herstellen der Verbindung zu verwendende Authentifizierungsmethode fest.  
  
 Weitere Informationen zu SPNs finden Sie unter [Dienst Prinzipal Namen &#40;SPNs&#41; in Client Verbindungen &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Dokumentierte SQL_COPT_SS_BROWSE_CACHE_DATA.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlbrowseconnetct-Funktion](https://go.microsoft.com/fwlink/?LinkId=59329)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
