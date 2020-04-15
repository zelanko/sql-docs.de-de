---
title: LÖSCHEN TAG Befehl | Microsoft Docs
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
ms.openlocfilehash: 97ca5abca7e70f5dffdae9bf14ce64429fd203d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303541"
---
# <a name="delete-tag-command"></a>DELETE TAG-Befehl
Entfernt ein Oder ein Tag aus einer zusammengesetzten Indexdatei (.cdx).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Argumente  
 *TagName1* VON *CDXFileName1*[, *TagName2*[OF *CDXFileName2*]] ]] ...  
 Gibt ein Tag an, das aus einer zusammengesetzten Indexdatei entfernt werden soll. Sie können mehrere Tags mit einer DELETE TAG löschen, indem Sie eine Liste von Tag-Namen einschließen, die durch Kommas getrennt sind. Wenn zwei oder mehr Tags mit demselben Namen in den geöffneten Indexdateien vorhanden sind, können Sie ein Tag aus einer bestimmten Indexdatei entfernen, indem Sie OF *CDXFileName*einschließen.  
  
 ALLE [OF *CDXFileName*]  
 Entfernt jedes Tag aus einer zusammengesetzten Indexdatei. Wenn die aktuelle Tabelle über eine strukturelle zusammengesetzte Indexdatei verfügt, werden alle Tags aus der Indexdatei entfernt, die Indexdatei wird vom Datenträger gelöscht, und das Flag im Kopf der Tabelle, das das Vorhandensein einer zugeordneten strukturverknüpften Zusammengesetztenindexdatei angibt, wird entfernt. Verwenden Sie ALLE mit OF *CDXFileName,* um alle Tags aus einer geöffneten zusammengesetzten Indexdatei zu entfernen, die nicht die strukturell zusammengesetzte Indexdatei ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Zusammengesetzte Indexdateien, die mit INDEX erstellt wurden, enthalten Tags, die Indexeinträgen entsprechen. DELETE TAG wird verwendet, um ein Oder ein Tag aus geöffneten zusammengesetzten Indexdateien zu entfernen. Sie können nur Tags aus zusammengesetzten Indexdateien löschen, die im aktuellen Arbeitsbereich geöffnet sind. Wenn Sie alle Tags aus einer zusammengesetzten Indexdatei entfernen, wird die Datei vom Datenträger gelöscht.  
  
 Visual FoxPro sucht zuerst nach einem Tag in der Strukturverbindungsindexdatei (falls eine geöffnet ist). Wenn sich das Tag nicht in der Strukturverbindungsindexdatei befindet, sucht Visual FoxPro nach dem Tag in den anderen geöffneten zusammengesetzten Indexdateien.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehl INDEX](../../odbc/microsoft/index-command.md)
