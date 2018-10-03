---
title: Execute21-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute21 method [RDS]
ms.assetid: 9f131c8d-1497-416d-8209-abb481c38f7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab67abb878cd5eea91aff9c8d055baec0ef87329
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717148"
---
# <a name="execute21-method-rds"></a>Execute21-Methode (RDS)
Führt die Anforderung und erstellt ein ADO-Recordset für die Verwendung in ADO 2.1.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Execute21(ConnectionString As String, HandlerString As String, QueryString As String, lMarshalOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine Zeichenfolge, die für die Verbindung der OLE DB-Anbieter für die Ausführung wird, in dem die Anforderung gesendet werden. Wenn ein Handler mithilfe des Parameters *HandlerString*, können sie bearbeiten oder Ersetzen Sie die Verbindungszeichenfolge.  
  
 *HandlerString*  
 Die Zeichenfolge identifiziert, den Handler, der mit dieser Ausführung verwendet werden. Die Zeichenfolge besteht aus zwei Teilen. Der erste Teil enthält den Namen (ProgID) des Handlers verwendet werden. Der zweite Teil der Zeichenfolge enthält Argumente, die an den Handler übergeben werden. Wie die Argumentzeichenfolge interpretiert wird, ist bestimmten Handler. Die beiden Teile sind durch die erste Instanz eines Kommas in der Zeichenfolge getrennt, (obwohl die Argumentzeichenfolge zusätzliche Kommas enthalten kann). Die Argumente sind optional.  
  
 *QueryString*  
 Ein Befehl in der Befehlssprache, die vom OLE DB-Anbieters identifiziert, die in der Verbindungszeichenfolge unterstützt wird. Für SQL-basierte Anbieter, er enthält möglicherweise eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] Befehls-Anweisung, aber dies eventuell nicht möglich, für nicht-SQL-Anbieter (z. B. MSDataShape) eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] abfrageanweisung.  
  
 Wenn ein Handler verwendet wird (und es wird dringend empfohlen, dass ein Ereignishandler verwendet werden), kann der Handler auch ändern oder Ersetzen Sie den hier angegebenen Wert. Der Handler in der Regel ersetzt z.B. *QueryString* mit einer Abfragezeichenfolge aus der Initialisierungsdatei. Standardmäßig wird die Datei "Msdfmap.ini" verwendet.  
  
 *lMarshalOptions*  
 Zum Festlegen von der Marshallen-Optionen für das Rowset/Recordset, das zurückgegeben wird.  
  
 *TableID*  
 Geben Sie eine Variante des VT_EMPTY oder VT_BSTR. Wenn dieser Wert des Typs VT_EMPTY ist, wird sie ignoriert. Ist vom Typ VT_BSTR, wird das Recordset mithilfe erstellt **AdCmdTableDirect** hier über den angegebenen Wert und die *QueryString* Parameter wird ignoriert.  
  
 *lExecuteOptions*  
 Eine Bitmaske von Optionen:  
  
 1 =*ReadOnly* Öffnen des Recordsets mit **AdLockReadOnly**.  
  
 2 =*NoBatch* Öffnen des Recordsets mit **AdLockOptimistic**.  
  
 4 =*AllParamInfoSupplied* der Aufrufer garantiert Parameterinformationen für alle Parameter angegeben wird, im *pParameters*.  
  
 8 =*GetInfo* Parameterinformationen für die Abfrage wird vom OLE DB-Anbieter abgerufen und zurückgegeben, die der *pParameters* Parameter. Die Abfrage nicht ausgeführt wird und kein Recordset wird zurückgegeben.  
  
 16 = GetHiddenColumns Öffnen des Recordsets mit **AdLockBatchOptimistic** und ausgeblendeten Spalten werden in das Recordset enthalten sein.  
  
 Obwohl *ReadOnly*, *NoBatch* und *GetHiddenColumns* sind sich gegenseitig ausschließende Optionen, es ist kein Fehler mehr als einer davon festgelegt. Wenn mehrere Optionen festgelegt werden, *GetHiddenColumns* hat Vorrang vor allen anderen Optionen, gefolgt von *ReadOnly*. Wenn keine Optionen, standardmäßig angegeben sind Öffnen des Recordsets mit **AdLockBatchOptimistic** ausgeblendete Spalten nicht im Recordset enthalten sind.  
  
 *pParameters*  
 Eine Variante, die ein sicheres Array von Parameterdefinitionen enthält. Wenn die *GetInfo* Option angegeben wurde, im *lExecuteOptions*, dieser Parameter wird verwendet, um die Parameterdefinitionen abgerufen, die vom OLE DB-Anbieter zurück. Andernfalls kann dieser Parameter leer sein.  
  
## <a name="remarks"></a>Hinweise  
 Die *HandlerString* Parameter kann null sein. Was in diesem Fall geschieht, hängt davon ab, wie die RDS-Server konfiguriert ist. Eine Zeichenfolge Handler "MSDFMAP.handler" gibt an, dass der Handler für Microsoft bereitgestellt (Msdfmap.dll) verwendet werden soll. Eine Zeichenfolge Handler "MASDFMAP.handler,sample.ini" gibt an, dass der Handler für Msdfmap.dll verwendet werden soll und das Argument "sample.ini" an den Ereignishandler übergeben werden sollen. MSDFMAP.dll interpretiert das Argument als eine Richtung auf die sample.ini verwenden, um die Verbindungs- und Zeichenfolgen zu überprüfen.  
  
> [!NOTE]
>  Die **Execute21** Methode ist eine Version der [Execute-Methode (RDS)](../../../ado/reference/rds-api/execute-method-rds.md). Müssen Sie verwenden die **Execute** Methode für die Kommunikation mit ADO 2.1, die **Execute21** -Methode stattdessen aufgerufen werden kann. Die Funktionen des die **Execute** -Methode in der ADO 2.5 und höher stellen eine Obermenge der Funktionen für die gleiche Methode in ADO 2.1 bereitgestellt.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


