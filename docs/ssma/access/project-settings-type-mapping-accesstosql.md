---
title: Projekteinstellungen (Typzuordnung) (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 01154cf477435e9dc5335606d0c11a05aecc492b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68066660"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Projekteinstellungen (Typzuordnung) (accesstosql)
Mit den Projekteinstellungen für die Typzuordnung können Sie Standardtypmappings für das SSMA-Projekt festlegen. Sie können auch Typzuordnungen für einzelne Datenbankobjekte angeben. Weitere Informationen finden Sie unter [Zuordnung von Quell-und Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md).  
  
Die Typzuordnung ist in den Dialogfeldern **Projekteinstellungen** und **Standard Projekteinstellungen** verfügbar:  
  
-   Verwenden Sie das Dialogfeld **Projekteinstellungen** , um Konfigurationsoptionen für das aktuelle Projekt festzulegen. Um auf die typzuordnungseinstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **Projekteinstellungen**aus, und klicken Sie dann im linken Bereich auf **Typzuordnung** .  
  
-   Verwenden Sie das Dialogfeld **Standard Projekteinstellungen** , um Konfigurationsoptionen für alle Projekte festzulegen. Um auf die typzuordnungseinstellungen zuzugreifen, wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus, wählen Sie den Migrations Projekttyp, für den die Einstellungen angezeigt werden müssen/Changed in der Dropdown Liste **Migrations Ziel Version** aus, und klicken Sie im linken Bereich auf **Typzuordnung** .  
  
## <a name="options"></a>Optionen  
**Quelltyp**  
Der zuzuordnende Zugriffs Datentyp.  
  
**Zieltyp**  
Der Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder SQL Azure Datentyp für den angegebenen Zugriffs Datentyp.  
  
Die folgende Tabelle zeigt die Standard Zuordnung zwischen Quell-und Ziel Datentypen.  
  
|Access-Datentyp|SQL Server-Datentyp|  
|--------------------|------------------------|  
|**binärer\*Wert [.. \*]**|**varbinary [\*]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**Währungs**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**LONGBINARY**|**varbinary(max)**|  
|**Memo**|**nvarchar(max)**|  
|**Memo** für Zugriff 97|**varchar(max)**|  
|**single**|**real**|  
|**Text [\*.. \*]**|**nvarchar [\*]**|  
|**Text [\*.. ] \*** -für Access 97|**varchar [\*]**|  
  
**Add (Hinzufügen)**  
Klicken Sie hier, um der Zuordnungsliste einen Datentyp hinzuzufügen.  
  
**Bearbeiten**  
Klicken Sie hierauf, um einen Datentyp in der Liste Zuordnung zu bearbeiten.  
  
**Remove**  
Klicken Sie hierauf, um die ausgewählte Datentyp Zuordnung aus der Liste Zuordnung zu entfernen.  
  
**Standard wiederherstellen**  
Klicken Sie hier, um alle Datentyp Zuordnungen auf die SSMA-Standardwerte zurückzusetzen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Zuordnen von Quell- und Zieldatentypen](mapping-source-and-target-data-types-accesstosql.md)  
[Referenz zur Benutzeroberfläche (Zugriff)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
