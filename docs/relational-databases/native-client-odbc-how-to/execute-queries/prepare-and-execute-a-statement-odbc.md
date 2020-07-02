---
title: Vorbereiten und Ausführen einer Anweisung (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7108bc20679957499626c121e5412090c8d5f1c2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725057"
---
# <a name="prepare-and-execute-a-statement-odbc"></a>Vorbereiten und Ausführen von Anweisungen (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a>So bereiten Sie eine Anweisung vor und führen sie dann mehrmals aus  
  
1.  Ruft die [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360) auf, um die Anweisung vorzubereiten.  
  
2.  Optional können Sie [sqlnumparser](https://go.microsoft.com/fwlink/?LinkId=58404) zum Ermitteln der Anzahl der Parameter in der vorbereiteten Anweisung aufzurufen.  
  
3.  Optional führen Sie für jeden Parameter in der vorbereiteten Anweisung Folgendes aus:  
  
    -   Aufrufen von [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) zum Abrufen von Parameterinformationen.  
  
    -   Binden Sie jeden Parameter mithilfe von [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md)an eine Programm Variable. Richten Sie alle Data-at-Execution-Parameter ein.  
  
4.  Für jede Ausführung einer vorbereiteten Anweisung gilt:  
  
    -   Wenn die Anweisung über Parametermarkierungen verfügt, fügen Sie die Datenwerte in den gebundenen Parameterpuffer ein.  
  
    -   Ruft [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) auf, um die vorbereitete Anweisung auszuführen.  
  
    -   Wenn Data-at-Execution-Eingabeparameter verwendet werden, gibt [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) SQL_NEED_DATA zurück. Senden Sie die Daten in Blöcken mithilfe von [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) und [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a>So bereiten Sie eine Anweisung mit spaltenweiser Parameterbindung vor  
  
1.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) auf, um die folgenden Attribute festzulegen:  
  
    -   Legen Sie SQL_ATTR_PARAMSET_SIZE auf die Anzahl von Sätzen (S) von Parametern fest.  
  
    -   Legen Sie SQL_ATTR_PARAM_BIND_TYPE auf SQL_PARAMETER_BIND_BY_COLUMN fest.  
  
    -   Legen Sie das SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut fest, um auf eine SQLUINTEGER-Variable zu zeigen und die Anzahl der verarbeiteten Parameter zu halten.  
  
    -   Legen Sie das SQL_ATTR_PARAMS_STATUS_PTR-Attribut fest, sodass es auf ein Array mit S SQLUSSMALLINT-Variablen zeigt, welche die Parameterstatusindikatoren enthalten.  
  
2.  Erstellen Sie SQLPrepare, um die Anweisung vorzubereiten.  
  
3.  Optional können Sie [sqlnumparser](https://go.microsoft.com/fwlink/?LinkId=58404) zum Ermitteln der Anzahl der Parameter in der vorbereiteten Anweisung aufzurufen.  
  
4.  Optional können Sie für jeden Parameter in der vorbereiteten Anweisung SQLDescribeParam aufrufen, um Parameterinformationen abzurufen.  
  
5.  Führen Sie folgende Aktionen für jeden Parametermarker durch:  
  
    -   Weisen Sie ein Array mit S-Parameterpuffern zu, um Datenwerte zu speichern.  
  
    -   Weisen Sie ein Array mit S-Parameterpuffern zu, um Datenlängen zu speichern.  
  
    -   Aufrufen von SQLBindParameter, um die Parameter Datenwert-und Daten Längen Arrays an den Anweisungs Parameter zu binden.  
  
    -   Falls der Parameter ein Data-at-Execution-Textparameter oder –Imageparameter ist, richten Sie ihn ein.  
  
    -   Wenn Data-at-Execution-Parameter verwendet werden, richten Sie sie ein.  
  
6.  Für jede Ausführung einer vorbereiteten Anweisung gilt:  
  
    -   Fügen Sie die S Datenwerte und S Datenlängen in die gebundenen Parameterarrays ein.  
  
    -   Rufen Sie SQLExecute auf, um die vorbereitete Anweisung auszuführen.  
  
    -   Wenn Data-at-Execution-Eingabeparameter verwendet werden, gibt SQLExecute SQL_NEED_DATA zurück. Senden Sie die Daten in Blöcken mithilfe von SQLParamData und SQLPutData.  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a>So bereiten Sie eine Anweisung mit zeilenweiser Parameterbindung vor  
  
1.  Ordnen Sie ein Array [S] von Strukturen zu, wobei S der Anzahl von Parametersätzen entspricht. Die Struktur verfügt über ein Element für jeden Parameter, und jedes Element verfügt über zwei Teile:  
  
    -   Der erste Teil ist eine Variable des entsprechenden Datentyps zum Speichern der Parameterdaten.  
  
    -   Der zweite Teil ist eine SQLINTEGER-Variable zum Speichern des Statusindikators.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) auf, um die folgenden Attribute festzulegen:  
  
    -   Legen Sie SQL_ATTR_PARAMSET_SIZE auf die Anzahl von Sätzen (S) von Parametern fest.  
  
    -   Legen Sie SQL_ATTR_PARAM_BIND_TYPE auf die Größe der in Schritt 1 zugeordneten Struktur fest.  
  
    -   Legen Sie das SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut fest, um auf eine SQLUINTEGER-Variable zu zeigen und die Anzahl der verarbeiteten Parameter zu halten.  
  
    -   Legen Sie das SQL_ATTR_PARAMS_STATUS_PTR-Attribut fest, sodass es auf ein Array mit S SQLUSSMALLINT-Variablen zeigt, welche die Parameterstatusindikatoren enthalten.  
  
3.  Erstellen Sie SQLPrepare, um die Anweisung vorzubereiten.  
  
4.  Aufrufen Sie für jede Parameter Markierung SQLBindParameter, um den Parameter Datenwert und den Daten Längen Zeiger auf die Variablen im ersten Element des Arrays mit Strukturen zu verweisen, die in Schritt 1 zugewiesen wurden. Falls der Parameter ein Data-at-Execution-Parameter ist, richten Sie ihn ein.  
  
5.  Für jede Ausführung einer vorbereiteten Anweisung gilt:  
  
    -   Füllen Sie das gebundene Parameterpufferarray mit Datenwerten.  
  
    -   Rufen Sie SQLExecute auf, um die vorbereitete Anweisung auszuführen. Der Treiber führt die SQL-Anweisung S Mal aus, einmal für jeden Parametersatz.  
  
    -   Wenn Data-at-Execution-Eingabeparameter verwendet werden, gibt SQLExecute SQL_NEED_DATA zurück. Senden Sie die Daten in Blöcken mithilfe von SQLParamData und SQLPutData.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst-wie-Themen zum Ausführen von Abfragen &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
