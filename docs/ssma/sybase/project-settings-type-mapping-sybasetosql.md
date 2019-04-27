---
title: Projekteinstellungen (Typzuordnung) (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 148180d95bcbff1626069e72fb66dd9a3ca859c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62667920"
---
# <a name="project-settings-type-mapping-sybasetosql"></a>Projekteinstellungen (Typzuordnung) (SybaseToSQL)
Die Seite Type Mapping der **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA für Sybase Adaptive Server Enterprise (ASE)-Datentypen in konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.  
  
Der Seite "Datentypzuordnung" steht in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Angeben der Einstellungen für die Zuordnung für alle zukünftigen SSMA-Projekten, auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen sind erforderlich, um die angezeigt werden oder geändert von **Migration Zielversion** Dropdownliste aus, und wählen Sie dann **Type Mapping** am unteren Rand im linken Bereich.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, und wählen Sie dann **Type Mapping** am unteren Rand im linken Bereich.  
  
## <a name="options"></a>Optionen  
**Quelltyp**  
Der zugeordnete ASE-Datentyp.  
  
**Zieltyp**  
Das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp für den angegebenen Typ der ASE-Daten.  
  
Finden Sie in der Tabelle im folgenden Abschnitt für den standardmäßigen SSMA für Sybase-Typzuordnung.  
  
**Hinzufügen**  
Klicken Sie auf diese Option, um einen Datentyp der Zuordnungsliste hinzuzufügen.  
  
**Bearbeiten**  
Klicken Sie auf diese Option, um den ausgewählten Datentyp in der Zuordnungsliste zu bearbeiten.  
  
**Entfernen**  
Klicken Sie auf diese Option, um die ausgewählte Zuordnung von Datentypen aus der Zuordnungsliste zu entfernen.  
  
**Standard wiederherstellen**  
Klicken Sie auf diese Option, um die Liste ' datentypzuordnung ' der SSMA-Standardwerte zurückzusetzen.  
  
## <a name="default-type-mapping"></a>Standardtypmapping  
Die folgende Tabelle enthält die Standard-Typzuordnung zwischen ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.  
  
|ASE-Datentyp|SQL Server-Datentyp|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**binary**|**binary**|  
|**Binary [\*... 8000]**|**binary[\*]**|  
|**binary[8001..\*]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**char**|**char**|  
|**char varying**|**varchar**|  
|**Char varying [\*... 8000]**|**varchar[\*]**|  
|**Char varying [8001..\*]**|**varchar(max)**|  
|**char[\*..8000]**|**char[\*]**|  
|**char[8001..\*;]**|**varchar(max)**|  
|**character**|**char**|  
|**unterschiedliche Zeichen**|**varchar**|  
|**unterschiedliche Zeichen [\*... 8000]**|**varchar[\*]**|  
|**unterschiedliche Zeichen [8001..\*]**|**varchar(max)**|  
|**Zeichen [\*... 8000]**|**char[\*]**|  
|**character[8001..\*]**|**varchar(max)**|  
|**Datum**|**Datum**|  
|**datetime**|**datetime2[3]**|  
|**dec**|**decimal**|  
|**DEC [\*... \*]**|**Dezimal [\*]**|  
|**dec[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**decimal**|**decimal**|  
|**Dezimal [\*... \*]**|**Dezimal [\*]**|  
|**Dezimal [\*... \*][\*.. \*]**|**decimal[\*][\*]**|  
|**mit doppelter Genauigkeit**|**float[53]**|  
|**float**|**float[53]**|  
|**"float" [\*... 15]**|**float[24]**|  
|**float[16..\*]**|**float[53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**integer**|**int**|  
|**longsysname**|**nvarchar[255]**|  
|**money**|**money**|  
|**National char**|**nchar**|  
|**National Char [\*... 4000]**|**nchar[\*]**|  
|**National Char varying**|**nvarchar**|  
|**National Char varying [\*... 4000]**|**nvarchar[\*]**|  
|**National Char varying [4001..\*]**|**nvarchar(max)**|  
|**National Char [4001..\*]**|**nvarchar(max)**|  
|**nationale Zeichensätze**|**nchar**|  
|**nationale Zeichensätze [\*... 4000]**|**nchar[\*]**|  
|**nationale Zeichensätze [4001..\*]**|**nvarchar(max)**|  
|**nationale Zeichensätze variieren.**|**nvarchar**|  
|**nationale Zeichensätze zu unterschiedlichen [\*... 4000]**|**nvarchar[\*]**|  
|**nationale Zeichensätze zu unterschiedlichen [4001..\*]**|**nvarchar(max)**|  
|**National varchar**|**nvarchar**|  
|**National Varchar [\*... 4000]**|**nvarchar[\*]**|  
|**National Varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**NCHAR variieren.**|**nvarchar**|  
|**NCHAR unterschiedliche [\*... 4000]**|**nvarchar[\*]**|  
|**NCHAR unterschiedliche [4001..\*]**|**nvarchar(max)**|  
|**NCHAR [\*... 4000]**|**nchar[\*]**|  
|**nchar[4001..\*]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**numerische [\*... \*]**|**numeric[\*]**|  
|**numerische [\*... \*][\*.. \*]**|**numeric[\*][\*]**|  
|**nvarchar**|**nvarchar**|  
|**Nvarchar [\*... 4000]**|**nvarchar[\*]**|  
|**nvarchar[4001..\*]**|**nvarchar(max)**|  
|**real**|**float[24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar[128]**|  
|**sysname[\*..\*]**|**nvarchar[255]**|  
|**text**|**text**|  
|**time**|**time[3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**unichar**|**nchar**|  
|**UNICHAR-variieren.**|**nvarchar**|  
|**unterschiedliche UNICHAR-[\*... 4000]**|**nvarchar[\*]**|  
|**unterschiedliche UNICHAR-[4001..\*]**|**nvarchar(max)**|  
|**UNICHAR [\*... 4000]**|**nchar[\*]**|  
|**unichar[4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar[\*..4000]**|**nvarchar[\*]**|  
|**univarchar[4001..\*]**|**nvarchar(max)**|  
|**unsigned bigint**|**numeric[20][0]**|  
|**unsigned int**|**bigint**|  
|**unsigned smallint**|**int**|  
|**unsigned tinyint**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**Varbinary [\*... 8000]**|**varbinary[\*]**|  
|**varbinary[8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**Varchar [\*... 8000]**|**varchar[\*]**|  
|**varchar[8001..\*]**|**varchar(max)**|  
  
