---
description: Richtlinien und Einschränkungen von DiffGrams für SQLXML
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
ms.openlocfilehash: 8a75caa96befa6705d76b5666e3e9a5ef9c131d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498520"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Richtlinien und Einschränkungen von DiffGrams für SQLXML
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Bei der Verwendung von DiffGrams mit SQLXML 4.0 gilt Folgendes:  
  
-   BLOB-Typen (Binary Large Object) wie **Text/ntext** und Bilder sollten nicht im- **\<diffgr:before>** Block in verwendet werden, wenn Sie mit DiffGrams arbeiten, da diese für die Verwendung in der Parallelitäts Steuerung eingeschlossen werden. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Beispielsweise wird das LIKE-Schlüsselwort in der WHERE-Klausel für den Vergleich zwischen Spalten des **Text** -Datentyps verwendet. Vergleiche schlagen jedoch bei BLOB-Typen fehl, bei denen die Größe der Daten größer als 8K ist.  
  
-   Sonderzeichen in **ntext** -Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4,0 verursachen. Beispielsweise schlägt die Verwendung von "[serialisierbar]" im **\<diffgr:before>** Block eines DiffGram bei Verwendung bei der Parallelitäts Prüfung einer Spalte vom Typ " **ntext** " mit der folgenden SQLOLEDB-Fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
