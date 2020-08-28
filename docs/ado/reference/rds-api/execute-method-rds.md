---
description: Execute-Methode (RDS)
title: Execute-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
author: rothja
ms.author: jroth
ms.openlocfilehash: 1be1721851bc5f0b969e8f38700ea1f63d91bbcc
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88982331"
---
# <a name="execute-method-rds"></a>Execute-Methode (RDS)
Führt die Anforderung aus und erstellt ein ADO-Recordset für die Verwendung in ADO 2,5 und höher.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Execute(ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation])  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine Zeichenfolge, die zum Herstellen einer Verbindung mit dem OLE DB Anbieter verwendet wird, an den die Anforderung zur Ausführung gesendet wird. Wenn ein Handler mithilfe von *handlerstring* angegeben wird, kann er die Verbindungs Zeichenfolge bearbeiten oder ersetzen.  
  
 *HandlerString*  
 Eine zweiteilige Zeichenfolge, die den Handler identifiziert, der bei dieser Ausführung verwendet werden soll. Die Zeichenfolge enthält zwei Teile. Der erste Teil enthält den Namen (ProgID) des zu verwendenden Handlers. Der zweite Teil enthält Argumente, die an den Handler übermittelt werden sollen. Die Details, wie die Argument Zeichenfolge interpretiert wird, sind spezifisch für jeden Handler. Die beiden Teile sind durch die erste Instanz eines Kommas in der Zeichenfolge getrennt. Die Argument Zeichenfolge kann zusätzliche Kommas enthalten. Die Argumente sind optional.  
  
 *QueryString*  
 Ein Befehl in der Befehlssprache, der von dem in der Verbindungs Zeichenfolge identifizierten OLE DB Anbieter unterstützt wird. Bei SQL-basierten Anbietern kann *QueryString* eine Transact-SQL-Befehls Anweisung enthalten, aber bei nicht-SQL-Anbietern (z. b. MSDataShape) kann dies keine [!INCLUDE[tsql](../../../includes/tsql-md.md)] Abfrage Anweisung sein.  
  
 Wenn ein Handler verwendet wird, kann der Handler den hier angegebenen Wert ändern oder ersetzen. Der-Handler ersetzt z. b. in der Regel *QueryString* durch eine Abfrage Zeichenfolge aus der INI-Datei. Standardmäßig wird die Msdfmap.ini Datei verwendet.  
  
 *lFetchOptions*  
 Gibt den Typ des asynchronen fetchen an.  
  
 Weitere Informationen finden Sie unter [FetchOptions-Eigenschaft (RDS)](./fetchoptions-property-rds.md).  
  
 *TableID*  
 Eine **Variante** vom Typ entweder VT_EMPTY oder VT_BSTR. Wenn dieser Wert vom Typ VT_EMPTY ist, wird er ignoriert. Wenn der Typ VT_BSTR ist, wird das Recordset mithilfe von **adCmdTableDirect** erstellt, und der hier angegebene Wert und der *QueryString* -Parameter werden ignoriert.  
  
 *lExecuteOptions*  
 Eine Bitmaske der Ausführungs Optionen:  
  
 1 =*Schreib* geschützt das Recordset wird mithilfe von **adlockread only**geöffnet.  
  
 2 =*nobatch* das Recordset wird mithilfe von **adlockoptimistisch**geöffnet.  
  
 4 =*allparaminfoist* der Aufrufer stellt sicher, dass Parameterinformationen für alle Parameter in *pparameters*angegeben werden.  
  
 8 =*GetInfo* -Parameterinformationen für die Abfrage werden vom OLE DB Anbieter abgerufen und im *pparameters* -Parameter zurückgegeben. Die Abfrage wird nicht ausgeführt, und es wird kein Recordset zurückgegeben.  
  
 16 =*gethiddencolumns* das Recordset wird mithilfe von **adlockbatchoptimier** geöffnet, und alle verborgenen Spalten werden in das Recordset eingeschlossen.  
  
 Schreibgeschützt, *nobatch* und *gethiddencolumns* sind Optionen, *die sich gegen*seitig ausschließen. Es wird jedoch kein Fehler generiert, wenn mehr als ein Wert festgelegt wird. Wenn mehrere Optionen festgelegt sind, hat *gethiddencolumns* Vorrang vor allen anderen, gefolgt *von "* schreibgeschützt". Wenn keine Optionen angegeben werden, wird das Recordset standardmäßig mithilfe von **adlockbatchoptimier** geöffnet, und verborgene Spalten sind nicht im Recordset enthalten.  
  
 *pParameters*  
 Eine **Variante** , die ein sicheres Array von Parameter Definitionen enthält. Wenn die *GetInfo* -Option in *lexecuteoptions*angegeben wurde, wird dieser Parameter verwendet, um die Parameter Definitionen zurückzugeben, die vom OLE DB Anbieter abgerufen werden. Andernfalls kann dieser Parameter leer sein.  
  
 *lcid*  
 Die LCID, die verwendet wird, um Fehler zu erstellen, die in *pinformation*zurückgegeben werden.  
  
 *pInformation*  
 Ein Zeiger auf Informationen, die von Execute zurückgegeben werden. Wenn der Wert NULL ist, werden keine Fehlerinformationen zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *handlerstring* -Parameter kann NULL sein. Was in diesem Fall geschieht, hängt von der Konfiguration des RDS-Servers ab. Die handlerzeichenfolge "msdfmap. Handler" gibt an, dass der von Microsoft bereitgestellte Handler (Msdfmap.dll) verwendet werden soll. Eine handlerzeichenfolge von "masdfmap. Handler, sample.ini" gibt an, dass der Msdfmap.dll Handler verwendet werden sollte und dass das Argument "sample.ini" an den Handler übermittelt werden soll. MSDFMAP.dll interpretiert das Argument als Richtung für die Verwendung des sample.ini, um die Verbindungs-und Abfrage Zeichenfolgen zu überprüfen.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](./datafactory-object-rdsserver.md)