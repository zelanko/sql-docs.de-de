---
title: Typzuordnung bearbeiten (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7078b4ed-c779-4bf3-8db8-f9dcb3edd50f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: b3857d2acda8f5c8b16f416987651db2b6b991b7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68264234"
---
# <a name="edit-type-mapping-oracletosql"></a>Bearbeiten der Typzuordnung (OracleToSQL)
Im Dialogfeld **Typzuordnung bearbeiten** können Sie angeben, wie Typen zwischen den Quell-und Ziel Datenbankobjekten zugeordnet werden sollen.  
  
Sie können auf dieses Dialogfeld an mehreren Stellen zugreifen:  
  
-   Wenn Sie eine Quelldatenbank oder ein Datenbankobjekt auswählen, wird rechts neben dem metadatenexplorer die Registerkarte **Typzuordnung** angezeigt. Klicken Sie zum Hinzufügen einer neuen Typzuordnung auf **Hinzufügen** , oder klicken Sie auf **Bearbeiten** , um eine vorhandene Typzuordnung zu ändern.  
  
-   Wählen Sie **im Menü Extras** die Option **Projekteinstellungen** oder **Standard Projekteinstellungen**aus. Wählen Sie im daraufhin angezeigten Dialogfeld die Option **Typzuordnung**aus. Klicken Sie zum Hinzufügen einer neuen Typzuordnung auf **Hinzufügen** , oder klicken Sie auf **Bearbeiten** , um eine vorhandene Typzuordnung zu ändern.  
  
Tabellen spezifische Typzuordnungen überschreiben Datenbank-und Projekttyp Zuordnungen. Datenbankspezifische Zuordnungen überschreiben Projekt Zuordnungen.  
  
## <a name="options"></a>Optionen  
**Quellentyp**  
Wählen Sie den Quell Datentyp aus, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem Datentyp zugeordnet werden soll.  
  
Wenn der Datentyp eine Variable Länge hat, werden die folgenden Felder unter **Quelltyp**angezeigt:  
  
**From**  
Geben Sie die Mindestlänge für diese Zuordnung an. Beispielsweise können Sie für den **NCHAR** -Datentyp 10 eingeben, um anzugeben, dass diese Zuordnung für einen Bereich gilt, der bei **NCHAR (10)** beginnt.  
  
**An**  
Geben Sie die maximale Länge für diese Zuordnung an. Beispielsweise können Sie für den **NCHAR** -Datentyp 20 eingeben, um anzugeben, dass diese Zuordnung für einen Bereich gilt, der bei **NCHAR (20)** endet.  
  
**Zieltyp**  
Wählen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Datentyp aus, dem der Quell Datentyp zugeordnet ist. Wenn SSMA die Tabelle oder die gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt, ändert sich der Quell Datentyp in diesen Datentyp.  
  
Wenn der Datentyp eine Variable Länge hat, wird das folgende Feld unter **Zieltyp**angezeigt:  
  
**Ersetzen durch**  
Geben Sie die Ziellänge für diese Zuordnung an. Beispielsweise können Sie für den Datentyp **nvarchar** den Wert 20 eingeben, um anzugeben, dass der angegebene Quell Datentyp **nvarchar (20)** zugeordnet werden soll.  
  
