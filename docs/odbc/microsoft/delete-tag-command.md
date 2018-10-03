---
title: TAG-Befehl DELETE | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bdef06ead8e4f9d9a8d012b2560c305ffcea009
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689718"
---
# <a name="delete-tag-command"></a>DELETE TAG-Befehl
Entfernt ein Tag oder Tags aus einer zusammengesetzten Index (CDX)-Datei an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Argumente  
 *TagName1*OF *CDXFileName1*[, *TagName2*[OF *CDXFileName2*]]...  
 Gibt eine Kennung an, um von einer zusammengesetzten Index entfernen. Sie können mehrere Tags mit einem löschen TAG löschen, indem Sie sowie eine Liste der Tag-Namen durch Kommas getrennt. Wenn mindestens zwei Transponder mit dem gleichen Namen in den Indexdateien öffnen vorhanden ist, können Sie ein Tag aus einem bestimmten Index-Datei entfernen, indem Sie einschließlich der *CDXFileName*.  
  
 ALLE [OF *CDXFileName*]  
 Entfernt alle Tags aus einer Datei zusammengesetzten Index. Wenn die aktuelle Tabelle eine strukturelle zusammengesetzten Index-Datei hat, werden alle Tags aus der Indexdatei entfernt, die Indexdatei wird vom Datenträger gelöscht und die Kennzeichen in den Tabellenkopf, der angibt, des Vorhandenseins einer Datei zugeordneten strukturelle zusammengesetzten Index entfernt werden. Verwendung mit der alle *CDXFileName* So entfernen Sie alle Tags aus einer Datei öffnen, zusammengesetzten Index als strukturelle zusammengesetzten Index-Datei.  
  
## <a name="remarks"></a>Hinweise  
 Zusammengesetzte Indexdateien, die mit dem INDEX erstellt, Indexeinträge für Tags enthalten. TAG löschen verwendet, um ein Tag oder Tags aus öffnen, zusammengesetzten Indexdateien zu entfernen. Sie können nur Tags aus zusammengesetzten Index im aktuellen Arbeitsbereich geöffneten Dateien löschen. Wenn Sie alle Tags aus einer Datei zusammengesetzten Index entfernen, wird die Datei vom Datenträger gelöscht.  
  
 Visual FoxPro sucht zuerst nach einem Tag in der Datei strukturelle zusammengesetzten Index, (Wenn eine geöffnet ist). Wenn Sie nicht das Tag in der Datei strukturelle zusammengesetzten Index ist, sucht Visual FoxPro für den Transponder in anderen Dateien öffnen, zusammengesetzten Index.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl INDEX](../../odbc/microsoft/index-command.md)
