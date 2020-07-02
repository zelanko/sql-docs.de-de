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
ms.openlocfilehash: 113090c317e88d3e9a7e7db2bfcb7d4d14b4ea1f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650069"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Richtlinien und Einschränkungen von DiffGrams für SQLXML
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Bei der Verwendung von DiffGrams mit SQLXML 4.0 gilt Folgendes:  
  
-   BLOB-Typen (Binary Large Object) wie **Text/ntext** und Bilder sollten nicht im- **\<diffgr:before>** Block in verwendet werden, wenn Sie mit DiffGrams arbeiten, da diese für die Verwendung in der Parallelitäts Steuerung eingeschlossen werden. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Beispielsweise wird das LIKE-Schlüsselwort in der WHERE-Klausel für den Vergleich zwischen Spalten des **Text** -Datentyps verwendet. Vergleiche schlagen jedoch bei BLOB-Typen fehl, bei denen die Größe der Daten größer als 8K ist.  
  
-   Sonderzeichen in **ntext** -Daten können aufgrund der Einschränkungen beim Vergleich von BLOB-Typen Probleme mit SQLXML 4,0 verursachen. Beispielsweise schlägt die Verwendung von "[serialisierbar]" im **\<diffgr:before>** Block eines DiffGram bei Verwendung bei der Parallelitäts Prüfung einer Spalte vom Typ " **ntext** " mit der folgenden SQLOLEDB-Fehlerbeschreibung fehl:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
