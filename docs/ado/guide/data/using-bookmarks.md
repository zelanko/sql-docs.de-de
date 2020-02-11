---
title: Verwenden von Lesezeichen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9fa2a738a3e94cd306619a318b75a2fd506972c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923603"
---
# <a name="using-bookmarks"></a>Verwenden von Textmarken
Es ist häufig nützlich, nach dem Verschieben in das **Recordset** direkt zu einem bestimmten Datensatz zurückzukehren, ohne durch jeden Datensatz scrollen und Werte vergleichen zu müssen. Wenn Sie z. b. versuchen, mit der **Find** -Methode nach einem Datensatz zu suchen, die Suche jedoch keine Datensätze zurückgibt, werden Sie automatisch an jedem Ende des **Recordsets**platziert. Wenn Ihr Anbieter diese unterstützt, können Sie Lesezeichen verwenden, um die Position zu markieren, bevor Sie die **Find** -Methode verwenden, um zu ihrem Speicherort zurückzukehren. Ein Lesezeichen ist ein **Variant** -Typwert, der einen Datensatz in einem **Recordset** -Objekt eindeutig identifiziert.  
  
 Sie können auch ein Variant-Array von Lesezeichen mit der **Recordset-Filter** Methode verwenden, um nach einem ausgewählten Satz von Datensätzen zu filtern. Weitere Informationen zu diesem Verfahren finden Sie unter Filtern der Ergebnisse im Thema [Arbeiten mit Recordsets](../../../ado/guide/data/working-with-recordsets.md)weiter unten in diesem Abschnitt.  
  
 Sie können die **Bookmark** -Eigenschaft verwenden, um ein Lesezeichen für einen Datensatz zu erhalten, oder den aktuellen Datensatz in einem **Recordset** -Objekt auf den Datensatz festlegen, der durch ein gültiges Lesezeichen identifiziert wird. Im folgenden Code wird die **Bookmark** -Eigenschaft verwendet, um ein Lesezeichen festzulegen, und dann nach dem Wechsel zu anderen Datensätzen zum Lesezeichen-Datensatz zurückzukehren. Verwenden Sie die **unterstützte** Methode, um zu bestimmen, ob Ihr **Recordset** Lesezeichen unterstützt.  
  
```  
'BeginBookmarkEg  
Dim varBookmark As Variant  
Dim blnCanBkmrk As Boolean  
  
objRs.Open strSQL, strConnStr, adOpenStatic, adLockOptimistic, adCmdText  
  
If objRs.RecordCount > 4 Then  
    objRs.Move 4                       ' move to the fifth record  
    blnCanBkmrk = objRs.Supports(adBookmark)  
    If blnCanBkmrk = True Then  
        varBookmark = objRs.Bookmark   ' record the bookmark  
        objRs.MoveLast                 ' move to a different record  
        objRs.Bookmark = varBookmark   ' return to the bookmarked (sixth) record  
    End If  
End If  
'EndBookmarkEg  
```  
  
 Die [unterstützte](../../../ado/reference/ado-api/supports-method.md) Methode wird später ausführlicher behandelt.  
  
 Mit Ausnahme der Groß-/Kleinschreibung von geklonten **Recordsets**sind Lesezeichen für das **Recordset** , in dem Sie erstellt wurden, eindeutig, auch wenn derselbe Befehl verwendet wird. Dies bedeutet, dass Sie kein **Lesezeichen** , das aus einem **Recordset** abgerufen wurde, verwenden können, um in einem zweiten **Recordset** , das mit demselben Befehl geöffnet wurde, zum gleichen Datensatz zu wechseln.
