---
description: CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse)
title: CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse)
ms.custom: seo-dt-2019
ms.date: 08/10/2017
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.assetid: 16ef8191-7587-45a3-9ee9-7d99b7088de3
author: ronortloff
ms.author: rortloff
ms.reviewer: jrasnick
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 841c8a62a90b6d14a1ee4d20bce7b57be097e9b9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88305004"
---
# <a name="create-remote-table-as-select-parallel-data-warehouse"></a>CREATE REMOTE TABLE AS SELECT (Parallel Data Warehouse)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Wählt Daten aus einer [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]-Datenbank und kopiert diese Daten in eine neue Tabelle in einer SMP-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank auf einem Remoteserver. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] verwendet die Appliance mit allen Vorteilen der MPP-Abfrageverarbeitung, um die Daten für die Remotekopie auszuwählen. Verwenden Sie diese Option für Szenarios, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionalität erfordern.  
  
 Informationen zum Konfigurieren des Remoteservers finden Sie unter „Remotetabellenkopie“ in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
CREATE REMOTE TABLE { database_name.schema_name.table_name | schema_name.table_name | table_name }  AT ('<connection_string>')  
    [ WITH ( BATCH_SIZE = batch_size ) ]  
    AS <select_statement>  
[;]  
  
<connection_string> ::=   
    Data Source = { IP_address | hostname } [, port ]; User ID = user_name ;Password = password;  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Die Datenbank zum Erstellen der Remotetabelle. *database_name* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank. Standardmäßig vorgegeben ist die Standarddatenbank für den Anmeldenamen des Benutzers auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zielinstanz.  
  
 *schema_name*  
 Das Schema der neuen Tabelle. Standardmäßig vorgegeben ist das Standardschema für den Anmeldenamen des Benutzers auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zielinstanz.  
  
 *table_name*  
 Der Name der neuen Tabelle. Informationen zu zulässigen Tabellennamen finden Sie unter "Objektbenennungsregeln" in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Die Remotetabelle wird als Heap erstellt. Sie verfügt weder über CHECK-Einschränkungen noch über Trigger. Die Sortierung der Remotetabellenspalten und die Sortierung der Spalten der Quelltabelle sind identisch. Dies gilt für Spalten der Typen **char**, **nchar**, **varchar** und **nvarchar**.  
  
 *connection_string*  
 Eine Zeichenfolge, die die Parameter `Data Source`, `User ID` und `Password` für das Herstellen einer Verbindung mit dem Remoteserver und der Datenbank angibt.  
  
 Die Verbindungszeichenfolge ist eine durch Semikola getrennte Liste von Schlüssel-Wert-Paaren. Bei Schlüsselwörtern muss die Groß-/Kleinschreibung nicht beachtet werden. Leerzeichen zwischen den Schlüssel-Wert-Paaren werden ignoriert. Allerdings muss bei Werten je nach Datenquelle möglicherweise die Groß-/Kleinschreibung beachtet werden.  
  
 *Data Source*  
 Der Parameter, der den Namen oder die IP-Adresse und die TCP-Portnummer für den SMP-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Remote-Instanz angibt.  
  
 *hostname* oder *IP_address*  
 Name des Remoteservercomputers oder IPv4-Adresse des Remoteservers. IPv6-Adressen werden nicht unterstützt. Sie können eine benannte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz im Format **Computer_Name\Instance_Name** oder **IP_address\Instance_Name** angeben. Der Server muss remote sein und kann daher nicht als „(local)“ angegeben werden.  
  
 TCP *port* number  
 Die für die Verbindung verwendete TCP-Portnummer. Sie können eine TCP-Portnummer zwischen 0 und 65535 für eine Instanz von SQL Server angeben, die nicht am Standardport 1433 lauscht. Beispiel: **ServerA,1450** oder **10.192.14.27,1435**  
  
> [!NOTE]  
>  Es wird empfohlen, die Verbindung mit dem Remoteserver über die IP-Adresse herzustellen. Je nach Netzwerkkonfiguration sind zur Herstellung einer Verbindung unter Angabe des Computernamens möglicherweise weitere Schritte erforderlich, damit Ihr nicht zur Appliance gehörender DNS-Server zum Auflösen des Namens in den korrekten Server verwendet werden kann. Dieser Schritt ist nicht erforderlich, wenn Sie die Verbindung mit einer IP-Adresse herstellen. Weitere Informationen finden Sie unter "Verwenden einer DNS-Weiterleitung zum Auflösen von DNS-Namen, die nicht zu Appliances gehören (Analytics Platform System)" in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 *user_name*  
 Eine gültige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmelde-ID für die Authentifizierung. Die maximale Anzahl von Zeichen ist 128.  
  
 *password*  
 Das Anmeldekennwort. Die maximale Anzahl von Zeichen ist 128.  
  
 *batch_size*  
 Die maximale Anzahl der Zeilen pro Batch. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] sendet Zeilen in Batches an den Zielserver. *Batch_size* ist eine positive ganze Zahl >=0. Standard ist "0".  
  
 WITH *common_table_expression*  
 Gibt ein temporäres benanntes Resultset an, das als allgemeiner Tabellenausdruck (CTE, Common Table Expression) bezeichnet wird. Weitere Informationen finden Sie unter [WITH common_table_expression &#40;Transact-SQL&#41;](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 SELECT \<select_criteria> Das Abfrageprädikat, das angibt, welche Daten die neue Remotetabelle auffüllen. Informationen zur SELECT-Anweisung finden Sie unter [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert:  
  
-   SELECT-Berechtigung für jedes Objekt in der SELECT-Klausel.  
  
-   CREATE TABLE-Berechtigung für die SMP-Zieldatenbank.  
  
-   ALTER-, INSERT- und SELECT-Berechtigungen für das SMP-Zielschema.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 Wenn das Kopieren von Daten für die Remotedatenbank fehlschlägt, bricht [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] den Vorgang ab, protokolliert einen Fehler und versucht, die Remotetabelle zu löschen. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] gewährleistet nicht die erfolgreiche Bereinigung der neuen Tabelle.  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
 **Remotezielserver**:  
  
-   TCP ist die Standardeinstellung und das einzige unterstützte Protokoll zum Herstellen einer Verbindung mit einem Remoteserver.  
  
-   Der Zielserver muss ein Server sein, der nicht zur Appliance gehört. CREATE REMOTE TABLE kann nicht verwendet werden, um Daten von einer Appliance auf eine andere zu kopieren.  
  
-   Die CREATE REMOTE TABLE-Anweisung erstellt lediglich neue Tabellen. Aus diesem Grund darf die neue Tabelle noch nicht vorhanden sein. Remotedatenbank und Remoteschema müssen bereits vorhanden sein.  
  
-   Der Remoteserver benötigt verfügbaren Speicherplatz zum Speichern der Daten, die von der Appliance zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Remotedatenbank übertragen werden.  
  
 **SELECT-Anweisung**:  
  
-   Die ORDER BY- und die TOP-Klausel werden nicht in den Auswahlkriterien unterstützt.  
  
-   CREATE REMOTE TABLE kann nicht innerhalb einer aktiven Transaktion und auch nicht dann ausgeführt werden, wenn die AUTOCOMMIT OFF-Einstellung für die Sitzung aktiv ist.  
  
 [SET ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/statements/set-rowcount-transact-sql.md) hat keine Auswirkung auf diese Anweisung. Verwenden Sie [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md), um ein ähnliches Verhalten zu erzielen.  
  
## <a name="locking-behavior"></a>Sperrverhalten  
 Nach dem Erstellen der Remotetabelle ist die Zieltabelle bis zum Start des Kopiervorgangs nicht gesperrt. Aus diesem Grund ist es möglich, dass ein anderer Prozess die Remotetabelle löscht, nachdem sie erstellt wurde und bevor der Kopiervorgang gestartet wird. In diesem Fall generiert [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] einen Fehler, und der Kopiervorgang schlägt fehl.  
  
## <a name="metadata"></a>Metadaten  
 Verwenden Sie [sys.dm_pdw_dms_workers &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md), um den Status des Kopiervorgangs der ausgewählten Daten auf den SMP-Remoteserver anzuzeigen. Zeilen mit dem Typ PARALLEL_COPY_READER enthalten diese Informationen.  
  
## <a name="security"></a>Sicherheit  
 CREATE REMOTE TABLE verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung, um eine Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Remote-Instanz herzustellen. Die Windows-Authentifizierung wird nicht verwendet.  
  
 Das von außen zugängliche Netzwerk [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] muss durch eine Firewall geschützt sein. Ausnahmen sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ports, administrative Ports und Managementports.  
  
 Zur Vermeidung versehentlicher Datenverluste oder -beschädigungen sollte das Benutzerkonto, das zum Kopieren von der Appliance in die Zieldatenbank verwendet wird, nur über die mindestens erforderlichen Berechtigungen für die Zieldatenbank verfügen.  
  
 Mithilfe der Verbindungseinstellungen können Sie eine Verbindung mit der SMP-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herstellen. Dabei sind Benutzername und Kennwortdaten SSL-geschützt, die eigentlichen Daten werden jedoch unverschlüsselt gesendet. In diesem Fall könnte ein böswilliger Benutzer den Text der CREATE REMOTE TABLE-Anweisung abfangen, der den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Benutzernamen und das Kennwort für die Anmeldung bei der SMP-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz enthält. Um dieses Risiko zu vermeiden, verwenden Sie die Verschlüsselung von Daten für die Verbindung mit der SMP-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
##  <a name="examples"></a><a name="Examples"></a> Beispiele  
  
### <a name="a-creating-a-remote-table"></a>A. Erstellen einer Remotetabelle  
 In diesem Beispiel wird eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-SMP-Remotetabelle, die `MyOrdersTable` heißt, in der Datenbank `OrderReporting` und dem Schema `Orders` erstellt. Die `OrderReporting`-Datenbank befindet sich auf einem Server mit dem Namen `SQLA`, der am Standardport 1433 lauscht. Die Verbindung mit dem Server verwendet die Anmeldeinformationen des Benutzers `David`, dessen Kennwort `e4n8@3` lautet.  
  
```  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
AS SELECT <select_criteria>;  
```  
  
### <a name="b-querying-the-sysdm_pdw_dms_workers-dmv-for-remote-table-copy-status"></a>B. Abfragen der sys.dm_pdw_dms_workers-DMV nach dem Kopierstatus der Remotetabelle  
 Diese Abfrage zeigt, wie der Kopierstatus für eine Remotetabellenkopie angezeigt wird.  
  
```  
SELECT * FROM sys.dm_pdw_dms_workers   
WHERE type = 'PARALLEL_COPY_READER';  
```  
  
### <a name="c-using-a-query-join-hint-with-create-remote-table"></a>C. Verwenden eines Join-Abfragehinweises mit CREATE REMOTE TABLE  
 Diese Abfrage zeigt die grundlegende Syntax für die Verwendung eines Join-Abfragehinweises mit CREATE REMOTE TABLE. Nachdem die Abfrage an den Steuerungsknoten übermittelt wurde, wendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (wird auf den Computeknoten ausgeführt) die Hashjoinstrategie an, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Abfrageplan generiert wird. Weitere Informationen zu Join-Abfragehinweisen und zur Verwendung der OPTION-Klausel finden Sie unter [OPTION-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
USE ssawPDW;  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
    AS SELECT T1.* FROM OrderReporting.Orders.MyOrdersTable T1   
    JOIN OrderReporting.Order.Customer T2  
    ON T1.CustomerID=T2.CustomerID OPTION (HASH JOIN);  
```  
  
  

