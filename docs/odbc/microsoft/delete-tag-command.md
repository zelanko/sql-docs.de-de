---
description: DELETE TAG-Befehl
title: Befehl zum Löschen von Tags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16eeedd8d9995cf636791688179ba21002411aea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340886"
---
# <a name="delete-tag-command"></a>DELETE TAG-Befehl
Entfernt ein Tag oder Tags aus einer Verbund Indexdatei (. CDX).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Argumente  
 *TagName1* Of *CDXFileName1*[, *TagName2*[of *CDXFileName2*]]...  
 Gibt ein Tag an, das aus einer Verbund Indexdatei entfernt werden soll. Sie können mehrere Tags mit einem DELETE-Tag löschen, indem Sie eine Liste von Tagnamen einschließen, die durch Kommas getrennt sind. Wenn zwei oder mehr Tags mit dem gleichen Namen in den geöffneten Indexdateien vorhanden sind, können Sie ein Tag aus einer bestimmten Indexdatei entfernen, indem Sie *cdxfilename*einschließen.  
  
 Alle [von *cdxfilename*]  
 Entfernt jedes Tag aus einer Verbund Indexdatei. Wenn die aktuelle Tabelle über eine Struktur zusammengesetzte Indexdatei verfügt, werden alle Tags aus der Indexdatei entfernt, die Indexdatei wird vom Datenträger gelöscht, und das-Flag im Header der Tabelle, das angibt, dass eine zugeordnete Struktur zusammengesetzter Indexdatei entfernt wird. Verwenden Sie all with von *cdxfilename* , um alle Tags aus einer geöffneten Verbund Indexdatei zu entfernen, die nicht die Struktur der zusammengesetzten Indizes ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Zusammengesetzte Indexdateien, die mit Index erstellt wurden, enthalten Tags, die den Indexeinträgen entsprechen. Das Tag "Delete" wird verwendet, um ein Tag oder Tags aus geöffneten Verbund Indexdateien zu entfernen. Sie können nur Tags aus Verbund Indexdateien löschen, die im aktuellen Arbeitsbereich geöffnet sind. Wenn Sie alle Tags aus einer Verbund Indexdatei entfernen, wird die Datei vom Datenträger gelöscht.  
  
 Visual FoxPro sucht zuerst nach einem Tag in der Struktur der zusammengesetzten Indexdatei (sofern eine solche geöffnet ist). Wenn das-Tag nicht in der Struktur der zusammengesetzten Indexdatei ist, sucht Visual FoxPro in den anderen geöffneten Verbund Indexdateien nach dem-Tag.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehl INDEX](../../odbc/microsoft/index-command.md)
