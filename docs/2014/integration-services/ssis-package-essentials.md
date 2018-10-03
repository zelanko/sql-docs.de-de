---
title: SSIS-Paket Essentials | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 91aa24a11c7d4587500ab7154f582bb47b8f8c4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193240"
---
# <a name="ssis-package-essentials"></a>SSIS-Paketgrundlagen
  Ein Paket ist das Objekt, das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Funktionalität zum Extrahieren, Transformieren und Laden von Daten implementiert. Ein Paket lässt sich mit dem [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]erstellen. Sie können ein Paket aber auch mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Import/Export-Assistenten oder dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Verbindungsprojekt-Assistenten erstellen. Weitere Informationen [Erstellen von Paketen in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) im SSIS-Designer und [Berichtsimport-Assistent](../../2014/integration-services/import-project-wizard.md).  
  
 Ein Basispaket enthält die folgenden Elemente:  
  
 **Ablaufsteuerungselemente**  
 Diese erforderlichen Elemente führen verschiedene Funktionen aus, stellen Struktur bereit, und kontrollieren die Reihenfolge, in der Elemente ausgeführt werden. Die Hauptablaufsteuerungselemente sind Tasks, Container und Rangfolgeneinschränkungen. Es muss wenigstens ein Ablaufsteuerungselement in einem Paket geben.  
  
 Weitere Informationen finden Sie unter [Control Flow](control-flow/control-flow.md).  
  
 **Datenflusselemente**  
 Diese optionalen Elemente extrahieren Daten, ändern Daten und laden Daten in Datenquellen. Die Hauptdatenflusselemente sind Quellen, Transformationen und Ziele. In einem Paket müssen keine Datenflusselemente enthalten sein.  
  
 Weitere Informationen finden Sie unter [Data Flow](data-flow/data-flow.md).  
  
 Ein Beispiel zum Erstellen eines einfachen Pakets finden Sie unter [Lektion 1: Erstellen des Projekts und Basispakets](lesson-1-create-a-project-and-basic-package-with-ssis.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Erstellen von Paketen in SQL Server-Datentools](create-packages-in-sql-server-data-tools.md)  
  
-   [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [Hinzufügen oder Löschen einer Komponente im Datenfluss](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
1.  Video [Erstellen eines Basispakets (SQL Server-Video)](http://go.microsoft.com/fwlink/?LinkId=131023)auf msdn.microsoft.com.  
  
## <a name="see-also"></a>Siehe auch  
 [Integrationsdienste &#40;SSIS&#41; Pakete](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md)  
  
  
