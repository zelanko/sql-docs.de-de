---
description: Execute21-Methode (RDS)
title: Execute21-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute21 method [RDS]
ms.assetid: 9f131c8d-1497-416d-8209-abb481c38f7b
author: rothja
ms.author: jroth
ms.openlocfilehash: 84c8c977615fdc99da45a255e5306d4066b13406
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88982311"
---
# <a name="execute21-method-rds"></a>Execute21-Methode (RDS)
Führt die Anforderung aus und erstellt ein ADO-Recordset für die Verwendung in ADO 2,1.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Execute21(ConnectionString As String, HandlerString As String, QueryString As String, lMarshalOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine Zeichenfolge, die zum Herstellen einer Verbindung mit dem OLE DB Anbieter verwendet wird, an den die Anforderung zur Ausführung gesendet wird. Wenn ein Handler mithilfe von *handlerstring*angegeben wird, kann die Verbindungs Zeichenfolge bearbeitet oder ersetzt werden.  
  
 *HandlerString*  
 Die Zeichenfolge identifiziert den Handler, der bei dieser Ausführung verwendet werden soll. Die Zeichenfolge enthält zwei Teile. Der erste Teil enthält den Namen (ProgID) des zu verwendenden Handlers. Der zweite Teil der Zeichenfolge enthält Argumente, die an den Handler übermittelt werden sollen. Wie die Argument Zeichenfolge interpretiert wird, ist handlerspezifisch. Die beiden Teile sind durch die erste Instanz eines Kommas in der Zeichenfolge getrennt (obwohl die Argument Zeichenfolge zusätzliche Kommas enthalten kann). Die Argumente sind optional.  
  
 *QueryString*  
 Ein Befehl in der Befehlssprache, der von dem in der Verbindungs Zeichenfolge identifizierten OLE DB Anbieter unterstützt wird. Bei SQL-basierten Anbietern kann es eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] Befehls Anweisung enthalten, aber bei nicht-SQL-Anbietern (z. b. MSDataShape) ist dies möglicherweise keine [!INCLUDE[tsql](../../../includes/tsql-md.md)] Abfrage Anweisung.  
  
 Außerdem kann der Handler den hier angegebenen Wert ändern oder ersetzen, wenn ein Handler verwendet wird (und es dringend empfohlen wird, einen Handler zu verwenden). Der-Handler ersetzt z. b. in der Regel *QueryString* durch eine Abfrage Zeichenfolge aus der INI-Datei. Standardmäßig wird die Msdfmap.ini Datei verwendet.  
  
 *lMarshalOptions*  
 Wird verwendet, um die Marshallingoptionen für das Rowset/Recordset festzulegen, das zurückgegeben wird.  
  
 *TableID*  
 Eine Variante vom Typ entweder VT_EMPTY oder VT_BSTR. Wenn dieser Wert vom Typ VT_EMPTY ist, wird er ignoriert. Wenn der Typ VT_BSTR ist, wird das Recordset mithilfe von **adCmdTableDirect** erstellt, wobei der hier angegebene Wert verwendet wird und der *QueryString* -Parameter ignoriert wird.  
  
 *lExecuteOptions*  
 Eine Bitmaske der Ausführungs Optionen:  
  
 1 =*Schreib* geschützt das Recordset wird mithilfe von **adlockread only**geöffnet.  
  
 2 =*nobatch* das Recordset wird mithilfe von **adlockoptimistisch**geöffnet.  
  
 4 =*allparaminfoist* der Aufrufer stellt sicher, dass Parameterinformationen für alle Parameter in *pparameters*angegeben werden.  
  
 8 =*GetInfo* -Parameterinformationen für die Abfrage werden vom OLE DB Anbieter abgerufen und im *pparameters* -Parameter zurückgegeben. Die Abfrage wird nicht ausgeführt, und es wird kein Recordset zurückgegeben.  
  
 16 = gethiddencolumns das Recordset wird mithilfe von **adlockbatchoptimier** geöffnet, und alle verborgenen Spalten werden in das Recordset eingeschlossen.  
  
 Obwohl "read *only*", " *nobatch* " und " *gethiddencolumns* " sich gegenseitig ausschließende Optionen sind, ist es nicht möglich, mehr als eine dieser Optionen festzulegen. Wenn mehrere Optionen festgelegt sind, hat *gethiddencolumns* Vorrang vor allen anderen Optionen, gefolgt *von "* schreibgeschützt". Wenn keine Optionen angegeben werden, wird das Recordset standardmäßig mithilfe von **adlockbatchoptimierup** geöffnet, aber verborgene Spalten sind nicht im Recordset enthalten.  
  
 *pParameters*  
 Eine Variante, die ein sicheres Array von Parameter Definitionen enthält. Wenn die *GetInfo* -Option in *lexecuteoptions*angegeben wurde, wird dieser Parameter verwendet, um die Parameter Definitionen zurückzugeben, die vom OLE DB Anbieter abgerufen werden. Andernfalls ist dieser Parameter möglicherweise leer.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *handlerstring* -Parameter kann NULL sein. Was in diesem Fall geschieht, hängt von der Konfiguration des RDS-Servers ab. Die handlerzeichenfolge "msdfmap. Handler" gibt an, dass der von Microsoft bereitgestellte Handler (Msdfmap.dll) verwendet werden soll. Eine handlerzeichenfolge von "masdfmap. Handler, sample.ini" gibt an, dass der Msdfmap.dll Handler verwendet werden sollte und dass das Argument "sample.ini" an den Handler übermittelt werden soll. MSDFMAP.dll interpretiert das Argument als Richtung für die Verwendung des sample.ini, um die Verbindungs-und Abfrage Zeichenfolgen zu überprüfen.  
  
> [!NOTE]
>  Die **Execute21** -Methode ist eine Version der [Execute-Methode (RDS)](./execute-method-rds.md). Wenn Sie die **Execute** -Methode für die Kommunikation mit ADO 2,1 verwenden müssen, kann stattdessen die **Execute21** -Methode aufgerufen werden. Die Funktionen der **Execute** -Methode in ADO 2,5 und höher sind eine supermenge der Funktionen, die für dieselbe Methode in ADO 2,1 bereitgestellt werden.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](./datafactory-object-rdsserver.md)