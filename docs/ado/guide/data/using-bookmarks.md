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
manager: craigg
ms.openlocfilehash: a083f9d411474769335fdfae32bd59dfe455a9f8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660638"
---
# <a name="using-bookmarks"></a>Verwenden von Textmarken
Es ist häufig nützlich, um direkt zu einem bestimmten Datensatz zurückgegeben wird, nach dem verschoben haben, der **Recordset** ohne zu scrollen Sie durch jeden Datensatz und Vergleichen von Werten. Z. B., wenn Sie versuchen, suchen Sie für einen Datensatz mit den **finden** -Methode, aber die Suche keine Datensätze zurückgibt, wird automatisch am Ende des der **Recordset**. Wenn Ihr Anbieter unterstützt werden, können Lesezeichen verwendet werden, markieren Sie Ihre aktuelle Position vor der Verwendung der **finden** Methode, sodass Sie für Ihren Standort wiederherstellen können. Ein Lesezeichen ist ein **Variant** Typwert, die eindeutig einen Datensatz in einem **Recordset** Objekt.  
  
 Sie können auch ein variant-Array von Lesezeichen mit dem **Recordset-Filter** Methode, um für eine ausgewählte Gruppe von Datensätzen zu filtern. Ausführliche Informationen zu diesem Verfahren finden Sie Filtern der Ergebnisse im Thema [arbeiten mit Recordsets](../../../ado/guide/data/working-with-recordsets.md)weiter unten in diesem Abschnitt.  
  
 Können Sie die **Lesezeichen** Eigenschaft, die ein Lesezeichen für einen Eintrag zu erhalten, oder legen Sie den aktuellen Datensatz in einer **Recordset** Objekt, das den Datensatz, der durch ein gültiges Lesezeichen identifiziert wird. Der folgende code verwendet die **Lesezeichen** Eigenschaft, um ein Lesezeichen festlegen, und klicken Sie dann auf den mit Lesezeichen markierten Eintrag verschieben in einen anderen Datensätzen zurückgeben. Bestimmt, ob Ihre **Recordset** unterstützt Lesezeichen, verwenden die **unterstützt** Methode.  
  
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
  
 Die [unterstützt](../../../ado/reference/ado-api/supports-method.md) Methode wird später ausführlicher behandelt.  
  
 Außer bei geklonten **Recordsets**, Lesezeichen gelten nur für die **Recordset** in dem sie erstellt wurden, auch wenn Sie der gleiche Befehl verwendet wird. Dies bedeutet, dass Sie kein **Lesezeichen** abgerufen, die von einem **Recordset** zum Verschieben auf den gleichen Datensatz in einer Sekunde **Recordset** mit den gleichen Befehl geöffnet.
