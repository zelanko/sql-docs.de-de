---
title: Projekteinstellungen (Typzuordnung) (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 12002496f30d836f01d0b11f4007f63f018266e9
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87930728"
---
# <a name="project-settings-type-mapping-sybasetosql"></a>Projekteinstellungen (Typzuordnung) (SybaseToSQL)
Die Seite Typzuordnung des Dialog Felds **Projekteinstellungen** enthält Einstellungen, die anpassen, wie SSMA die Datentypen von Sybase Adaptive Server Enterprise (ASE) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen konvertiert.  
  
Die Seite Typzuordnung ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar.  
  
-   Wenn Sie die typzuordnungseinstellungen für alle zukünftigen SSMA-Projekte angeben möchten, wählen Sie **im Menü Extras die Option** **Standard Projekteinstellungen**aus, wählen Sie den Migrations Projekttyp aus, für den die Einstellungen in der Dropdown Liste **Migrations Ziel Version** angezeigt oder geändert werden müssen, und wählen Sie dann unten im linken Bereich **Typzuordnung** aus.  
  
-   Um Einstellungen für das aktuelle Projekt anzugeben, wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus, und klicken Sie dann unten im linken Bereich auf **Typzuordnung** .  
  
## <a name="options"></a>Optionen  
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
  
**Standard wiederherstellen**  
Klicken Sie hier, um die Liste Typzuordnung auf die SSMA-Standardwerte zurückzusetzen.  
  
## <a name="default-type-mapping"></a>Standardtypmapping  
Die folgende Tabelle enthält die Standardtyp Zuordnung zwischen ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen.  
  
|ASE-Datentyp|SQL Server-Datentyp|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**binary**|**binary**|  
|**binärer Wert [ \* .. 8000]**|**Binary [ \* ]**|  
|**Binary [8001.. \* ]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**char**|**char**|  
|**char varying**|**varchar**|  
|**char-Variation [ \* .. 8000]**|**varchar [ \* ]**|  
|**char-Variation [8001.. \* ]**|**varchar(max)**|  
|**Char [ \* .. 8000]**|**Char [ \* ]**|  
|**Char [8001... \* ]**|**varchar(max)**|  
|**Art**|**char**|  
|**character varying**|**varchar**|  
|**variierendes Zeichen [ \* .. 8000]**|**varchar [ \* ]**|  
|**variierendes Zeichen [8001.. \* ]**|**varchar(max)**|  
|**Zeichen [ \* .. 8000]**|**Char [ \* ]**|  
|**Zeichen [8001.. \* ]**|**varchar(max)**|  
|**date**|**date**|  
|**datetime**|**datetime2 [3]**|  
|**31.12.2012**|**decimal**|  
|**Dez [ \* .. \* ]**|**Dezimalzahl [ \* ]**|  
|**Dez [ \* .. \* ] [\*..\*]**|**Dezimal [ \* ] [ \* ]**|  
|**decimal**|**decimal**|  
|**Dezimal [ \* .. \* ]**|**Dezimalzahl [ \* ]**|  
|**Dezimal [ \* .. \* ] [\*..\*]**|**Dezimal [ \* ] [ \* ]**|  
|**double precision**|**float [53]**|  
|**float**|**float [53]**|  
|**float [ \* .. 17.15**|**float [24]**|  
|**float [16.. \* ]**|**float [53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**integer**|**int**|  
|**longsysname**|**nvarchar [255]**|  
|**money**|**money**|  
|**National Char**|**nchar**|  
|**National Char [ \* .. 4000]**|**NCHAR [ \* ]**|  
|**nationale char-Variation**|**nvarchar**|  
|**National char Variation [ \* .. 4000]**|**nvarchar [ \* ]**|  
|**National char Variation [4001.. \* ]**|**nvarchar(max)**|  
|**National Char [4001.. \* ]**|**nvarchar(max)**|  
|**Länder Zeichen**|**nchar**|  
|**Länder Zeichen [ \* .. 4000]**|**NCHAR [ \* ]**|  
|**Länder Zeichen [4001.. \* ]**|**nvarchar(max)**|  
|**unterschiedliches Zeichen**|**nvarchar**|  
|**unterschiedlicher nationaler Zeichen [ \* .. 4000]**|**nvarchar [ \* ]**|  
|**unterschiedliches Zeichen [4001.. \* ]**|**nvarchar(max)**|  
|**National varchar**|**nvarchar**|  
|**National varchar [ \* .. 4000]**|**nvarchar [ \* ]**|  
|**National varchar [4001.. \* ]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**NCHAR-Variation**|**nvarchar**|  
|**NCHAR variiert [ \* .. 4000]**|**nvarchar [ \* ]**|  
|**NCHAR-Variation [4001.. \* ]**|**nvarchar(max)**|  
|**NCHAR [ \* .. 4000]**|**NCHAR [ \* ]**|  
|**NCHAR [4001.. \* ]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**numerisch [ \* .. \* ]**|**numerisch [ \* ]**|  
|**numerisch [ \* .. \* ] [\*..\*]**|**numerisch [ \* ] [ \* ]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar [ \* .. 4000]**|**nvarchar [ \* ]**|  
|**nvarchar [4001.. \* ]**|**nvarchar(max)**|  
|**real**|**float [24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar [128]**|  
|**sysname [ \* .. \* ]**|**nvarchar [255]**|  
|**text**|**text**|  
|**time**|**Zeit [3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**UNICHAR**|**nchar**|  
|**UNICHAR-Variation**|**nvarchar**|  
|**UNICHAR variiert [ \* .. 4000]**|**nvarchar [ \* ]**|  
|**UNICHAR Variation [4001.. \* ]**|**nvarchar(max)**|  
|**UNICHAR [ \* .. 4000]**|**NCHAR [ \* ]**|  
|**UNICHAR [4001.. \* ]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar [ \* .. 4000]**|**nvarchar [ \* ]**|  
|**univarchar [4001.. \* ]**|**nvarchar(max)**|  
|**nicht signiertes bigint**|**numerisch [20] [0]**|  
|**unsigned int**|**bigint**|  
|**smallint ohne Vorzeichen**|**int**|  
|**nicht signiertes tinyint**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary [ \* .. 8000]**|**varbinary [ \* ]**|  
|**varbinary [8001.. \* ]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar [ \* .. 8000]**|**varchar [ \* ]**|  
|**varchar [8001.. \* ]**|**varchar(max)**|  
  
