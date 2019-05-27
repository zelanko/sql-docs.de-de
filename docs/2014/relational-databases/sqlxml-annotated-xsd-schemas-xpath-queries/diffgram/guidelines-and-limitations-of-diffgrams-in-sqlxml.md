---
title: Richtlinien und Einschränkungen von DiffGrams für SQLXML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1113bf11fcb3b1be2164bc6e685e6454323f3df
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66013061"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Richtlinien und Einschränkungen von DiffGrams für SQLXML
  Bei der Verwendung von DiffGrams mit SQLXML 4.0 gilt Folgendes:  
  
-   BLOB-Typen (Binary Large Object), wie zum Beispiel `text/ntext`, und Images sollten nicht im `<diffgr:before>`-Block verwendet werden, wenn Sie mit DiffGrams arbeiten, da sie auf diese Weise für die Verwendung in der Parallelitätssteuerung eingeschlossen werden. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Das gilt zum Beispiel für das LIKE-Schlüsselwort in der WHERE-Klausel zwischen Spalten des `text`-Datentyps. Vergleiche schlagen allerdings für BLOB-Typen fehl, deren Datengröße 8 K übersteigt.  
  
-   Sonderzeichen in `ntext`-Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4.0 verursachen. Die Verwendung von "[Serializable]" im `<diffgr:before>`-Block eines DiffGrams, das in der Parallelitätsprüfung einer Spalte vom Typ `ntext` verwendet wird, schlägt beispielsweise mit der folgenden SQLOLEDB-Fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
