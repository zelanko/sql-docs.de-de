---
title: SQLBrowseConnect | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
caps.latest.revision: 55
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93fdfd34974916e67b218f53408596ca649693ba
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421869"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
  **SQLBrowseConnect** Schlüsselwörter, die kategorisiert werden können in drei Ebenen von Verbindungsinformationen verwendet. In der folgenden Tabelle wird für jedes Schlüsselwort angegeben, ob eine Liste gültiger Werte zurückgegeben wird und ob das Schlüsselwort optional ist.  
  
## <a name="level-1"></a>Ebene 1  
  
|Schlüsselwort|Liste zurückgegeben?|Optional?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DSN|–|nein|Name der Datenquelle zurückgegebene **SQLDataSources**. Das DSN-Schlüsselwort kann nicht verwendet werden, wenn das DRIVER-Schlüsselwort verwendet wird.|  
|DRIVER|–|nein|Microsoft® [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treibername ist {[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11}. Das DRIVER-Schlüsselwort kann nicht verwendet werden, wenn das DSN-Schlüsselwort verwendet wird.|  
  
## <a name="level-2"></a>Ebene 2  
  
|Schlüsselwort|Liste zurückgegeben?|Optional?|Description|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|ja|nein|Name des Servers in dem Netzwerk, auf dem die Datenquelle gespeichert ist. Für den Server kann der Begriff "(local)" eingegeben werden. In diesem Fall kann eine lokale Kopie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden, auch wenn dies keine vernetzte Version ist.|  
|UID|nein|ja|Benutzeranmelde-ID.|  
|PWD|nein|Ja (vom Benutzer abhängig)|Vom Benutzer angegebenes Kennwort.|  
|APP|nein|ja|Name der aufrufenden Anwendung **SQLBrowseConnect**.|  
|WSID|nein|ja|Workstation-ID. Dies ist normalerweise der Netzwerkname des Computers, auf dem die Anwendung ausgeführt wird.|  
  
## <a name="level-3"></a>Ebene 3  
  
|Schlüsselwort|Liste zurückgegeben?|Optional?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|ja|ja|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank.|  
|LANGUAGE|ja|ja|Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendete Landessprache.|  
  
 **SQLBrowseConnect** ignoriert die Werte der Schlüsselwörter DATABASE und LANGUAGE in den ODBC-Datenquellendefinitionen gespeichert. Wenn die Datenbank oder in der Verbindungszeichenfolge angegebene Sprache an übergeben **SQLBrowseConnect** ist ungültig, **SQLBrowseConnect** gibt SQL_NEED_DATA sowie die Verbindungsattribute der Ebene 3.  
  
 Die folgenden Attribute, die festgelegt werden, durch den Aufruf [SQLSetConnectAttr](sqlsetconnectattr.md), bestimmen Sie das Resultset zurückgegebenes **SQLBrowseConnect**.  
  
|attribute|Description|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Wenn diese Option auf SQL_MORE_INFO_YES festgelegt wird **SQLBrowseConnect** eine erweiterte Zeichenfolge mit Servereigenschaften zurück.<br /><br /> Folgendes ist ein Beispiel für eine erweiterte Zeichenfolge, die vom **SQLBrowseConnect**: Servername\instanzname; Gruppiert: Nein; Version: 8.00.131<br /><br /> In dieser Zeichenfolge werden verschiedene durch Semikolons getrennte Informationen zum Server aufgeführt. Informationen zu verschiedenen Serverinstanzen werden durch Kommas getrennt.|  
|SQL_COPT_SS_BROWSE_SERVER|Wenn ein Servername angegeben wird, **SQLBrowseConnect** Informationen für den angegebenen Server zurück. Wenn SQL_COPT_SS_BROWSE_SERVER NULL festgelegt ist **SQLBrowseConnect** gibt Informationen für alle Server in der Domäne zurück.<br /><br /> Aufgrund von Netzwerkproblemen **SQLBrowseConnect** erhalten möglicherweise nicht rechtzeitige eine Antwort von allen Servern. Daher kann die Liste der zurückgegebenen Server bei jeder Anforderung unterschiedlich sein.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Wenn die Pufferlänge nicht groß genug ist, um das Ergebnis aufzunehmen, können Sie das Attribut SQL_COPT_SS_BROWSE_CACHE_DATA auf SQL_CACHE_DATA_YES festlegen und Daten in Abschnitten abrufen. Diese Länge wird in das Argument Pufferlänge SQLBrowseConnect angegeben.<br /><br /> Wenn weitere Daten verfügbar sind, wird SQL_NEED_DATA zurückgegeben. Wenn keine weiteren Daten abrufbar sind, wird SQL_SUCCESS zurückgegeben.<br /><br /> Der Standardwert ist SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>SQLBrowseConnect-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall  
 Weitere Informationen zur Verwendung von **SQLBrowseConnect** zum Herstellen einer Verbindung mit einer [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, finden Sie unter [SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>SQLBrowseConnect-Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPNs)  
 Wenn eine Verbindung geöffnet wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client legt SQL_COPT_SS_MUTUALLY_AUTHENTICATED und SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD auf die zum Öffnen der Verbindung verwendete Authentifizierungsmethode fest.  
  
 Weitere Informationen zu SPNs finden Sie unter [Service Principal Names &#40;SPNs&#41; in Clientverbindungen &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Dokumentierte SQL_COPT_SS_BROWSE_CACHE_DATA.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQLBrowseConnect-Funktion](http://go.microsoft.com/fwlink/?LinkId=59329)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
