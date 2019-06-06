---
title: Execute-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5c0fa79bdf5acc89b7d884afa604ab08e926d9e1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707704"
---
# <a name="execute-method-rds"></a>Execute-Methode (RDS)
Führt die Anforderung und erstellt ein ADO-Recordset für die Verwendung in ADO, 2.5 und höher.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Execute(ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation])  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine Zeichenfolge, die für die Verbindung der OLE DB-Anbieter für die Ausführung wird, in dem die Anforderung gesendet werden. Wenn ein Handler mithilfe des Parameters *HandlerString* können sie bearbeiten oder Ersetzen Sie die Verbindungszeichenfolge.  
  
 *HandlerString*  
 Ein mit dem zweiteiligen-Zeichenfolge, die den Handler, der mit dieser Ausführung zu verwendende identifiziert. Die Zeichenfolge besteht aus zwei Teilen. Der erste Teil enthält den Namen (ProgID) des Handlers verwendet werden. Der zweite Teil enthält Argumente, die an den Handler übergeben werden. Die Details der Interpretation der Argumentzeichenfolge sind spezifisch für jeden Handler. Die beiden Teile sind durch die erste Instanz eines Kommas in der Zeichenfolge getrennt. Die Zeichenfolge mit Befehlsargumenten kann zusätzliche Kommas enthalten. Die Argumente sind optional.  
  
 *QueryString*  
 Ein Befehl in der Befehlssprache, die vom OLE DB-Anbieters identifiziert, die in der Verbindungszeichenfolge unterstützt wird. Für SQL-basierten Anbieter *QueryString* möglicherweise eine Transact-SQL-Befehl-Anweisung enthalten, aber dies eventuell nicht möglich, für nicht-SQL-Anbieter (z. B. MSDataShape) eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] abfrageanweisung.  
  
 Wenn ein Handler verwendet wird, kann der Handler ändern oder Ersetzen Sie den Wert, der hier angegebene. Der Handler in der Regel ersetzt z.B. *QueryString* mit einer Abfragezeichenfolge aus der Initialisierungsdatei. Standardmäßig wird die Datei "Msdfmap.ini" verwendet.  
  
 *lFetchOptions*  
 Gibt den Typ des asynchronen abrufen.  
  
 Weitere Informationen finden Sie unter [FetchOptions-Eigenschaft (RDS)](../../../ado/reference/rds-api/fetchoptions-property-rds.md).  
  
 *TableID*  
 Ein **Variant** vom Typ entweder VT_EMPTY oder VT_BSTR. Wenn dieser Wert des Typs VT_EMPTY ist, wird sie ignoriert. Ist vom Typ VT_BSTR, wird das Recordset mithilfe erstellt **AdCmdTableDirect** und der hier angegebene Wert und die *QueryString* Parameter wird ignoriert.  
  
 *lExecuteOptions*  
 Eine Bitmaske von Optionen:  
  
 1 =*ReadOnly* Öffnen des Recordsets mit **AdLockReadOnly**.  
  
 2 =*NoBatch* Öffnen des Recordsets mit **AdLockOptimistic**.  
  
 4 =*AllParamInfoSupplied* der Aufrufer garantiert Parameterinformationen für alle Parameter angegeben wird, im *pParameters*.  
  
 8 =*GetInfo* Parameterinformationen für die Abfrage wird vom OLE DB-Anbieter abgerufen und zurückgegeben, die der *pParameters* Parameter. Die Abfrage nicht ausgeführt wird und kein Recordset wird zurückgegeben.  
  
 16 =*GetHiddenColumns* Öffnen des Recordsets mit **AdLockBatchOptimistic** und ausgeblendeten Spalten werden in das Recordset enthalten sein.  
  
 *ReadOnly*, *NoBatch* und *GetHiddenColumns* sind sich gegenseitig ausschließende Optionen; allerdings generiert keine Fehler, um mehr als einer davon festzulegen. Wenn mehrere Optionen festgelegt werden, *GetHiddenColumns* hat Vorrang vor allen anderen gefolgt von *ReadOnly*. Wenn keine Optionen, standardmäßig angegeben sind Öffnen des Recordsets mit **AdLockBatchOptimistic** ausgeblendete Spalten nicht im Recordset enthalten sind.  
  
 *pParameters*  
 Ein **Variant** , ein sicheres Array von Parameterdefinitionen enthält. Wenn die *GetInfo* Option angegeben wurde, im *lExecuteOptions*, dieser Parameter wird verwendet, um die Parameterdefinitionen abgerufen, die vom OLE DB-Anbieter zurück. Andernfalls kann dieser Parameter leer sein.  
  
 *lcid*  
 Die LCID verwendet, um Fehler zu erstellen, die zurückgegeben werden *pInformation*.  
  
 *pInformation*  
 Ein Zeiger auf die von Execute zurückgegebenen Informationsfehler. Wenn der Wert NULL ist, wird keine Fehlerinformationen zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die *HandlerString* Parameter kann null sein. Was in diesem Fall geschieht, hängt davon ab, wie die RDS-Server konfiguriert ist. Eine Zeichenfolge Handler "MSDFMAP.handler" gibt an, dass der Handler für Microsoft bereitgestellt (Msdfmap.dll) verwendet werden soll. Eine Zeichenfolge Handler "MASDFMAP.handler,sample.ini" gibt an, dass der Handler für Msdfmap.dll verwendet werden soll und das Argument "sample.ini" an den Ereignishandler übergeben werden sollen. MSDFMAP.dll interpretiert das Argument als eine Richtung auf die sample.ini verwenden, um die Verbindungs- und Zeichenfolgen zu überprüfen.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


