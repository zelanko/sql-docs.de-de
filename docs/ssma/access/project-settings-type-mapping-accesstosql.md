---
title: Projekteinstellungen (Typzuordnung) (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0403c7074df0f81081cda167fe9bbf04626f2522
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985742"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Projekteinstellungen (Typzuordnung) (AccessToSQL)
Die projekteinstellungen Type Mapping können Sie die standardtypmappings für das SSMA-Projekt festgelegt. Sie können auch die replikationsdatentyp-Zuordnungen für einzelne Objekte angeben. Weitere Informationen finden Sie unter [Zuordnen von Quell- und Ziel-Datentypen](http://msdn.microsoft.com/b362a075-16e7-423f-b63f-e1e9f02844a9).  
  
Zuordnung eines Typs finden Sie in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder:  
  
-   Verwenden der **Projekteinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für das aktuelle Projekt. Einstellungen für die Zuordnung, für den Zugriff auf die **Tools** , wählen Sie im Menü **Projekteinstellungen**, und klicken Sie dann auf **Typzuordnung** im linken Bereich.  
  
-   Verwenden der **Projekt Standardeinstellungen** Dialogfeld zum Festlegen von Konfigurationsoptionen für alle Projekte. Einstellungen für die Zuordnung, für den Zugriff auf die **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, angezeigt oder geändert werden,  **Migration Zielversion** Dropdownliste aus, und klicken Sie dann auf **Type Mapping** im linken Bereich.  
  
## <a name="options"></a>Tastatur  
**Quelltyp**  
Der Access-Datentyp zugeordnet werden soll.  
  
**Zieltyp**  
Das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Datentyp für den angegebenen Datentyp für den Zugriff.  
  
Die folgende Tabelle zeigt die Zuordnung zwischen Quelle und Ziel-Datentypen.  
  
|Access-Datentyp|SQL Server-Datentyp|  
|--------------------|------------------------|  
|**Binary [\*... \*]**|**varbinary[\*]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**Währung**|**money**|  
|**Datum**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**GUID**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**longbinary**|**varbinary(max)**|  
|**Memo**|**nvarchar(max)**|  
|**Memo** Access 97:|**varchar(max)**|  
|**einzelne**|**real**|  
|**Text [\*... \*]**|**Nvarchar [\*]**|  
|**Text [\*... \*]** – für Access 97|**Varchar [\*]**|  
  
**Hinzufügen**  
Klicken Sie auf diese Option, um einen Datentyp der Zuordnungsliste hinzuzufügen.  
  
**Bearbeiten**  
Klicken Sie auf diese Option, um einen Datentyp aus der Zuordnung zu bearbeiten.  
  
**Entfernen**  
Klicken Sie auf diese Option, um die ausgewählte Zuordnung von Datentypen aus der Zuordnungsliste zu entfernen.  
  
**Auf Standard zurücksetzen**  
Klicken Sie auf diese Option, um alle datentypzuordnungen der SSMA-Standardwerte zurückzusetzen.  
  
## <a name="see-also"></a>Siehe auch  
[Mapping Source and Target Data Types (Zuordnen von Quell- und Zieldatentypen)](http://msdn.microsoft.com/b362a075-16e7-423f-b63f-e1e9f02844a9)  
[Benutzer-Schnittstelle Reference(Access)](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
