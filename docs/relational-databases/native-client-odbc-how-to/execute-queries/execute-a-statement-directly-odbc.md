---
title: Direktes Ausführen einer Anweisung (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a5ece0a8b0e0844e8c33779796b0217ebf744050
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73781427"
---
# <a name="execute-a-statement-directly-odbc"></a>Direktes Ausführen von Anweisungen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>So führen Sie eine Anweisung direkt und nur einmal aus  
  
1.  Wenn die Anweisung über Parameter Markierungen verfügt, verwenden Sie [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) , um jeden Parameter an eine Programm Variable zu binden. Füllen Sie die Programmvariablen mit Datenwerten, und richten Sie dann alle Data-at-Execution-Parameter ein.  
  
2.  Führen Sie [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) aus, um die Anweisung auszuführen.  
  
3.  Wenn Data-at-Execution-Eingabeparameter verwendet werden, gibt [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) SQL_NEED_DATA zurück. Senden Sie die Daten in Blöcken mithilfe von [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) und [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  

### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>So führen Sie mit der spaltenweisen Parameterbindung eine Anweisung mehrmals aus  
  
1.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) auf, um die folgenden Attribute festzulegen:  
  
     Legen Sie SQL_ATTR_PARAMSET_SIZE auf die Anzahl von Sätzen (S) von Parametern fest.  
  
     Legen Sie SQL_ATTR_PARAM_BIND_TYPE auf SQL_PARAMETER_BIND_BY_COLUMN fest.  
  
     Legen Sie das SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut fest, um auf eine SQLUINTEGER-Variable zu zeigen und die Anzahl der verarbeiteten Parameter zu halten.  
  
     Legen Sie SQL_ATTR_PARAMS_STATUS_PTR fest, um auf ein Array [S] aus SQLUSSMALLINT-Variablen zu zeigen und die Parameterstatusindikatoren zu halten.  
  
2.  Führen Sie folgende Aktionen für jeden Parametermarker durch:  
  
     Weisen Sie ein Array mit S-Parameterpuffern zu, um Datenwerte zu speichern.  
  
     Weisen Sie ein Array mit S-Parameterpuffern zu, um Datenlängen zu speichern.  
  
     Aufrufen von [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) , um die Parameter Datenwert-und Daten Längen Arrays an den Anweisungs Parameter zu binden.  
  
     Richten Sie alle Data-at-Execution-Text- oder Imageparameter ein.  
  
     Setzen Sie S-Datenwerte und S-Datenlängen in die gebundenen Parameterarrays ein.  
  
3.  Führen Sie [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) aus, um die Anweisung auszuführen. Der Treiber führt die Anweisung S-mal aus, einmal für jeden Parametersatz.  
  
4.  Wenn Data-at-Execution-Eingabeparameter verwendet werden, gibt [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) SQL_NEED_DATA zurück. Senden Sie die Daten in Blöcken mithilfe von [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) und [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>So führen Sie mit der zeilenweisen Parameterbindung eine Anweisung mehrmals aus  
  
1.  Ordnen Sie ein Array [S] von Strukturen zu, wobei S der Anzahl von Parametersätzen entspricht. Die Struktur verfügt über ein Element für jeden Parameter, und jedes Element verfügt über zwei Teile:  
  
     Der erste Teil ist eine Variable des entsprechenden Datentyps zum Speichern der Parameterdaten.  
  
     Der zweite Teil ist eine SQLINTEGER-Variable zum Speichern des Statusindikators.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) auf, um die folgenden Attribute festzulegen:  
  
     Legen Sie SQL_ATTR_PARAMSET_SIZE auf die Anzahl von Sätzen (S) von Parametern fest.  
  
     Legen Sie SQL_ATTR_PARAM_BIND_TYPE auf die Größe der in Schritt 1 zugeordneten Struktur fest.  
  
     Legen Sie das SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut fest, um auf eine SQLUINTEGER-Variable zu zeigen und die Anzahl der verarbeiteten Parameter zu halten.  
  
     Legen Sie SQL_ATTR_PARAMS_STATUS_PTR fest, um auf ein Array [S] aus SQLUSSMALLINT-Variablen zu zeigen und die Parameterstatusindikatoren zu halten.  
  
3.  Aufrufen Sie für jede Parameter Markierung [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) , um den Datenwert des Parameters und den Daten Längen Zeiger auf die Variablen im ersten Element des Arrays mit Strukturen zu verweisen, die in Schritt 1 zugewiesen wurden. Falls der Parameter ein Data-at-Execution-Parameter ist, richten Sie ihn ein.  
  
4.  Füllen Sie das gebundene Parameterpufferarray mit Datenwerten.  
  
5.  Führen Sie [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) aus, um die Anweisung auszuführen. Der Treiber führt die Anweisung S-mal aus, einmal für jeden Parametersatz.  
  
6.  Wenn Data-at-Execution-Eingabeparameter verwendet werden, gibt [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) SQL_NEED_DATA zurück. Senden Sie die Daten in Blöcken mithilfe von [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) und [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
 **Hinweis** Die Spalten-und zeilenweise Bindung wird in der Regel in Verbindung mit der [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360) und [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) als mit [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst-wie-Themen &#40;zum Ausführen von Abfragen ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
