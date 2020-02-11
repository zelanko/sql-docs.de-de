---
title: Projekteinstellungen (Typzuordnung) (sybasedesql) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028661"
---
# <a name="project-settings-type-mapping-sybasetosql"></a>Projekteinstellungen (Typzuordnung) (SybaseToSQL)
Die Seite Typzuordnung des Dialog Felds **Projekteinstellungen** enthält Einstellungen, die anpassen, wie SSMA die Datentypen von Sybase Adaptive Server Enterprise ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ASE) in Datentypen konvertiert.  
  
Die Seite Typzuordnung ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Wenn Sie die typzuordnungseinstellungen für alle zukünftigen SSMA-Projekte angeben möchten, wählen Sie **im Menü Extras die Option** **Standard Projekteinstellungen**aus, wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt oder geändert werden müssen, und wählen Sie dann unten im linken Bereich **Typzuordnung** aus.  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus, und klicken Sie dann unten im linken Bereich auf **Typzuordnung** .  
  
## <a name="options"></a>Tastatur  
**Quelltyp**  
Der zugeordnete ASE-Datentyp.  
  
**Zieltyp**  
Der Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp für den angegebenen ASE-Datentyp.  
  
In der Tabelle im folgenden Abschnitt finden Sie die standardmäßige SSMA für die Sybase-Typzuordnung.  
  
**Add (Hinzufügen)**  
Klicken Sie hier, um der Zuordnungsliste einen Datentyp hinzuzufügen.  
  
**Bearbeiten**  
Klicken Sie hierauf, um den ausgewählten Datentyp in der Liste Zuordnung zu bearbeiten.  
  
**Remove**  
Klicken Sie hierauf, um die ausgewählte Datentyp Zuordnung aus der Liste Zuordnung zu entfernen.  
  
**Auf Standard zurücksetzen**  
Klicken Sie hier, um die Liste Typzuordnung auf die SSMA-Standardwerte zurückzusetzen.  
  
## <a name="default-type-mapping"></a>Standardtyp Zuordnung  
Die folgende Tabelle enthält die Standardtyp Zuordnung zwischen ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Datentypen.  
  
|ASE-Datentyp|SQL Server-Datentyp|  
|-----------------|------------------------|  
|**BIGINT**|**BIGINT**|  
|**BINARY**|**BINARY**|  
|**binärer\*Wert [.. 8000]**|**Binary [\*]**|  
|**Binary [8001..\*]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**Char**|**Char**|  
|**char-Variation**|**varchar**|  
|**char-Variation\*[.. 8000]**|**varchar [\*]**|  
|**char-Variation [8001.\*.]**|**varchar(max)**|  
|**Char [\*.. 8000]**|**Char [\*]**|  
|**Char [8001..\*.]**|**varchar(max)**|  
|**Art**|**Char**|  
|**Zeichen variiert**|**varchar**|  
|**variierendes\*Zeichen [.. 8000]**|**varchar [\*]**|  
|**variierendes Zeichen [8001\*..]**|**varchar(max)**|  
|**Zeichen [\*.. 8000]**|**Char [\*]**|  
|**Zeichen [8001..\*]**|**varchar(max)**|  
|**date**|**date**|  
|**datetime**|**datetime2 [3]**|  
|**31.12.2012**|**Decimal**|  
|**Dez [\*... \*]**|**Dezimalzahl\*[]**|  
|**Dez [\*... \*][\*.. \*]**|**Dezimal [\*] [\*]**|  
|**Decimal**|**Decimal**|  
|**Dezimalwert\*[.. \*]**|**Dezimalzahl\*[]**|  
|**Dezimalwert\*[.. \*][\*.. \*]**|**Dezimal [\*] [\*]**|  
|**doppelte Genauigkeit**|**float [53]**|  
|**float**|**float [53]**|  
|**float [\*.. 17.15**|**float [24]**|  
|**float [16..\*]**|**float [53]**|  
|**Klang**|**Klang**|  
|**int**|**int**|  
|**integer**|**int**|  
|**longsysname**|**nvarchar [255]**|  
|**money**|**money**|  
|**National Char**|**nchar**|  
|**National Char [\*.. 4000]**|**NCHAR [\*]**|  
|**nationale char-Variation**|**nvarchar**|  
|**National char Variation [\*.. 4000]**|**nvarchar [\*]**|  
|**National char Variation [4001..\*]**|**nvarchar(max)**|  
|**National Char [4001..\*]**|**nvarchar(max)**|  
|**Länder Zeichen**|**nchar**|  
|**Länder Zeichen [\*.. 4000]**|**NCHAR [\*]**|  
|**Länder Zeichen [4001..\*]**|**nvarchar(max)**|  
|**unterschiedliches Zeichen**|**nvarchar**|  
|**unterschiedlicher nationaler Zeichen\*[.. 4000]**|**nvarchar [\*]**|  
|**unterschiedliches Zeichen [4001.\*.]**|**nvarchar(max)**|  
|**National varchar**|**nvarchar**|  
|**National varchar [\*.. 4000]**|**nvarchar [\*]**|  
|**National varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**NCHAR-Variation**|**nvarchar**|  
|**NCHAR variiert [\*.. 4000]**|**nvarchar [\*]**|  
|**NCHAR-Variation [4001.\*.]**|**nvarchar(max)**|  
|**NCHAR [\*.. 4000]**|**NCHAR [\*]**|  
|**NCHAR [4001..\*]**|**nvarchar(max)**|  
|**isch**|**isch**|  
|**numerisch\*[.. \*]**|**numerisch\*[]**|  
|**numerisch\*[.. \*][\*.. \*]**|**numerisch\*[]\*[]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar [\*.. 4000]**|**nvarchar [\*]**|  
|**nvarchar [4001..\*]**|**nvarchar(max)**|  
|**wirkliche**|**float [24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**SMALLMONEY**|**SMALLMONEY**|  
|**sysname**|**nvarchar [128]**|  
|**sysname [\*.. \*]**|**nvarchar [255]**|  
|**text**|**text**|  
|**time**|**Zeit [3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**UNICHAR**|**nchar**|  
|**UNICHAR-Variation**|**nvarchar**|  
|**UNICHAR variiert [\*.. 4000]**|**nvarchar [\*]**|  
|**UNICHAR Variation [4001..\*]**|**nvarchar(max)**|  
|**UNICHAR [\*.. 4000]**|**NCHAR [\*]**|  
|**UNICHAR [4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar [\*.. 4000]**|**nvarchar [\*]**|  
|**univarchar [4001..\*]**|**nvarchar(max)**|  
|**nicht signiertes bigint**|**numerisch [20] [0]**|  
|**Ganzzahl ohne Vorzeichen int**|**BIGINT**|  
|**smallint ohne Vorzeichen**|**int**|  
|**nicht signiertes tinyint**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary [\*.. 8000]**|**varbinary [\*]**|  
|**varbinary [8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar [\*.. 8000]**|**varchar [\*]**|  
|**varchar [8001..\*]**|**varchar(max)**|  
  
