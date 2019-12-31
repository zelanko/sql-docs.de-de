---
title: Richtlinien und Einschränkungen von DiffGrams für SQLXML
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eae0b81b3c55a4afe611cd8ed6fdbb495b498c61
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246598"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Richtlinien und Einschränkungen von DiffGrams für SQLXML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Bei der Verwendung von DiffGrams mit SQLXML 4.0 gilt Folgendes:  
  
-   BLOB-Typen (Binary Large Object) wie **Text/ntext** und Bilder sollten nicht in der ** \<diffgr verwendet werden: vor>** Block in, wenn Sie mit DiffGrams arbeiten, da Sie diese zur Verwendung in der Parallelitäts Steuerung einschließen. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Beispielsweise wird das LIKE-Schlüsselwort in der WHERE-Klausel für den Vergleich zwischen Spalten des **Text** -Datentyps verwendet. Vergleiche schlagen jedoch bei BLOB-Typen fehl, bei denen die Größe der Daten größer als 8K ist.  
  
-   Sonderzeichen in **ntext** -Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4,0 verursachen. Beispielsweise schlägt die Verwendung von "[serialisierbar]" im ** \<diffgr: Before>** -Block eines DiffGram bei Verwendung bei der Parallelitäts Prüfung einer Spalte vom Typ " **ntext** " mit der folgenden SQLOLEDB-Fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
