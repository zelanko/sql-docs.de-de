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
ms.openlocfilehash: d7b16bdf3717fa14f91af41663cbd65365eac52a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028661"
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
|**Char varying [\*... 8000]**|**Varchar [\*]**|  
|**Char varying [8001..\*]**|**varchar(max)**|  
|**Char [\*... 8000]**|**char[\*]**|  
|**char[8001..\*;]**|**varchar(max)**|  
|**character**|**char**|  
|**unterschiedliche Zeichen**|**varchar**|  
|**unterschiedliche Zeichen [\*... 8000]**|**Varchar [\*]**|  
|**unterschiedliche Zeichen [8001..\*]**|**varchar(max)**|  
|**Zeichen [\*... 8000]**|**char[\*]**|  
|**Zeichen [8001..\*]**|**varchar(max)**|  
|**date**|**date**|  
|**datetime**|**datetime2 [3]**|  
|**DEC**|**decimal**|  
|**DEC [\*... \*]**|**Dezimal [\*]**|  
|**dec[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**decimal**|**decimal**|  
|**Dezimal [\*... \*]**|**Dezimal [\*]**|  
|**Dezimal [\*... \*][\*.. \*]**|**decimal[\*][\*]**|  
|**mit doppelter Genauigkeit**|**float[53]**|  
|**float**|**float[53]**|  
|**"float" [\*... 15]**|**float[24]**|  
|**"float" [16..\*]**|**float[53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**integer**|**int**|  
|**longsysname**|**nvarchar[255]**|  
|**money**|**money**|  
|**National char**|**nchar**|  
|**National Char [\*... 4000]**|**nchar[\*]**|  
|**National Char varying**|**nvarchar**|  
|**National Char varying [\*... 4000]**|**Nvarchar [\*]**|  
|**National Char varying [4001..\*]**|**nvarchar(max)**|  
|**National Char [4001..\*]**|**nvarchar(max)**|  
|**nationale Zeichensätze**|**nchar**|  
|**nationale Zeichensätze [\*... 4000]**|**nchar[\*]**|  
|**nationale Zeichensätze [4001..\*]**|**nvarchar(max)**|  
|**nationale Zeichensätze variieren.**|**nvarchar**|  
|**nationale Zeichensätze zu unterschiedlichen [\*... 4000]**|**Nvarchar [\*]**|  
|**nationale Zeichensätze zu unterschiedlichen [4001..\*]**|**nvarchar(max)**|  
|**National varchar**|**nvarchar**|  
|**National Varchar [\*... 4000]**|**Nvarchar [\*]**|  
|**National Varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**NCHAR variieren.**|**nvarchar**|  
|**NCHAR unterschiedliche [\*... 4000]**|**Nvarchar [\*]**|  
|**NCHAR unterschiedliche [4001..\*]**|**nvarchar(max)**|  
|**NCHAR [\*... 4000]**|**nchar[\*]**|  
|**NCHAR [4001..\*]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**numerische [\*... \*]**|**numeric[\*]**|  
|**numerische [\*... \*][\*.. \*]**|**numeric[\*][\*]**|  
|**nvarchar**|**nvarchar**|  
|**Nvarchar [\*... 4000]**|**Nvarchar [\*]**|  
|**Nvarchar [4001..\*]**|**nvarchar(max)**|  
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
|**unterschiedliche UNICHAR-[\*... 4000]**|**Nvarchar [\*]**|  
|**unterschiedliche UNICHAR-[4001..\*]**|**nvarchar(max)**|  
|**UNICHAR [\*... 4000]**|**nchar[\*]**|  
|**UNICHAR [4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**Univarchar [\*... 4000]**|**Nvarchar [\*]**|  
|**Univarchar [4001..\*]**|**nvarchar(max)**|  
|**nicht signierte bigint**|**numeric[20][0]**|  
|**unsigned int**|**bigint**|  
|**nicht signierte smallint**|**int**|  
|**nicht signierte tinyint**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**Varbinary [\*... 8000]**|**varbinary[\*]**|  
|**varbinary[8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**Varchar [\*... 8000]**|**Varchar [\*]**|  
|**varchar[8001..\*]**|**varchar(max)**|  
  
