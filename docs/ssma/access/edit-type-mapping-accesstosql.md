---
title: Typzuordnung bearbeiten (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7f9d9530-6c04-41d9-bbe7-d91820a30066
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7d41fc2f01e2cfbc2b20c58ea9be640f2afd8ea0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006581"
---
# <a name="edit-type-mapping-accesstosql"></a>Typzuordnung bearbeiten (accesstosql)
Im Dialogfeld **Typzuordnung bearbeiten** können Sie angeben, wie Typen zwischen den Quell-und Ziel Datenbankobjekten zugeordnet werden sollen.  
  
Sie können auf dieses Dialogfeld an mehreren Stellen zugreifen:  
  
-   Wenn Sie eine Quelldatenbank oder ein Datenbankobjekt auswählen, wird rechts neben dem metadatenexplorer die Registerkarte **Typzuordnung** angezeigt. Klicken Sie zum Hinzufügen einer neuen Typzuordnung auf **Hinzufügen** , oder klicken Sie auf **Bearbeiten** , um eine vorhandene Typzuordnung zu ändern.  
  
-   Wählen Sie **im Menü Extras** die Option **Projekteinstellungen** oder **Standard Projekteinstellungen**aus. Wählen Sie im daraufhin angezeigten Dialogfeld die Option **Typzuordnung**aus. Klicken Sie zum Hinzufügen einer neuen Typzuordnung auf **Hinzufügen** , oder klicken Sie auf **Bearbeiten** , um eine vorhandene Typzuordnung zu ändern.  
  
Tabellen spezifische Typzuordnungen überschreiben Datenbank-und Projekttyp Zuordnungen. Datenbankspezifische Zuordnungen überschreiben Projekt Zuordnungen.  
  
## <a name="options"></a>Tastatur  
**Quelltyp**  
Wählen Sie den Quell Datentyp aus, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem Datentyp zugeordnet werden soll.  
  
Wenn der Datentyp eine Variable Länge hat, werden die folgenden Felder unter **Quelltyp**angezeigt:  
  
**Von**  
Geben Sie die Mindestlänge für diese Zuordnung an. Für den **Text** -Datentyp können Sie z. b. 10 eingeben, um anzugeben, dass diese Zuordnung für einen Bereich gilt, der bei **Text beginnt (10)**.  
  
**An**  
Geben Sie die maximale Länge für diese Zuordnung an. Für den **Text** -Datentyp können Sie z. b. 20 eingeben, um anzugeben, dass diese Zuordnung für einen Bereich gilt, der mit **Text endet (20)**.  
  
**Zieltyp**  
Wählen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Datentyp aus, dem der Quell Datentyp zugeordnet ist. Wenn SSMA die Tabelle oder die gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt, ändert sich der Quell Datentyp in diesen Datentyp.  
  
Wenn der Datentyp eine Variable Länge hat, wird das folgende Feld unter **Zieltyp**angezeigt:  
  
**Ersetzen durch**  
Geben Sie die Ziellänge für diese Zuordnung an. Beispielsweise können Sie für den Datentyp **nvarchar** den Wert 20 eingeben, um anzugeben, dass der angegebene Quell Datentyp **nvarchar (20)** zugeordnet werden soll.  
  
