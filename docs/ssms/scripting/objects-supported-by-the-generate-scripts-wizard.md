---
title: Vom Assistenten zum Generieren von Skripts unterstützte Objekte
description: Informationen dazu, welche Objekttypen der Assistent zum Generieren und Veröffentlichen von Skripts veröffentlichen kann
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a213efd1b0118e4313212b35aad943cbae50db2d
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246407"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Vom Assistenten zum Generieren von Skripts unterstützte Objekte
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Der Assistent zum Generieren und Veröffentlichen von Skripts unterstützt eine Teilmenge der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]unterstützten Objekte.  
  
## <a name="supported-objects"></a>Unterstützte Objekte  
 In der folgenden Tabelle finden Sie die Objekte, die vom Assistenten zum Generieren und Veröffentlichen von Skripts veröffentlicht werden können.  
  
:::row:::
    :::column:::
        Anwendungsrolle
    :::column-end:::
    :::column:::
        Datenbankrolle
    :::column-end:::
    :::column:::
        Schema
    :::column-end:::
    :::column:::
        Benutzerdefiniertes Aggregat
    :::column-end:::
    :::column:::
        Sicht*
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Assembly
    :::column-end:::
    :::column:::
        DEFAULT-Einschränkung
    :::column-end:::
    :::column:::
        Gespeicherte Prozedur*
    :::column-end:::
    :::column:::
        Benutzerdefinierter Datentyp
    :::column-end:::
    :::column:::
        XML-Schemaauflistung
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        CHECK-Einschränkung
    :::column-end:::
    :::column:::
        Volltextkatalog
    :::column-end:::
    :::column:::
        Synonym
    :::column-end:::
    :::column:::
        Benutzerdefinierte Funktion
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        CLR-gespeicherte Prozedur (Common Language Runtime)*
    :::column-end:::
    :::column:::
        Index
    :::column-end:::
    :::column:::
        Tabelle
    :::column-end:::
    :::column:::
        Benutzerdefinierte Tabelle
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        CLR-benutzerdefinierte Funktion
    :::column-end:::
    :::column:::
        Regel
    :::column-end:::
    :::column:::
        Benutzer**
    :::column-end:::
    :::column:::
        Benutzerdefinierter Typ
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

 *Ohne Verschlüsselung veröffentlicht.  
  
 **Alle Nicht-Systembenutzer in der Datenbank werden als Rollen veröffentlicht.  
  
  
