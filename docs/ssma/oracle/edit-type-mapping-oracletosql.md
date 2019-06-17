---
title: Bearbeiten der Typzuordnung (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7078b4ed-c779-4bf3-8db8-f9dcb3edd50f
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: ee8d2e4c16987f5cc012f734cdf649cde7f4ebb8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288574"
---
# <a name="edit-type-mapping-oracletosql"></a>Bearbeiten der Typzuordnung (OracleToSQL)
Die **Bearbeiten der Typzuordnung** Dialogfeld können Sie angeben, wie Datentypen zwischen Quelle und Ziel-Datenbankobjekten zugeordnet werden.  
  
Sie können dieses Dialogfeld an mehreren Stellen zugreifen:  
  
-   Bei Auswahl einer Quelldatenbank oder ein Datenbankobjekt, das **Type Mapping** Registerkarte wird rechts neben dem Metadaten-Explorer angezeigt. Klicken Sie auf **hinzufügen** fügen Sie eine neue Zuordnung hinzu, oder klicken Sie auf **bearbeiten** so ändern Sie eine vorhandene Typzuordnung.  
  
-   Auf der **Tools** , wählen Sie im Menü **Projekteinstellungen** oder **Projekt Standardeinstellungen**. Wählen Sie im daraufhin angezeigten Dialogfeld **Type Mapping**. Klicken Sie auf **hinzufügen** fügen Sie eine neue Zuordnung hinzu, oder klicken Sie auf **bearbeiten** so ändern Sie eine vorhandene Typzuordnung.  
  
Tabelle-spezifische Zuordnungen für Projekte replikationsdatentyp-Zuordnungen und Datenbank zu überschreiben. Datenbank-spezifische Zuordnungen überschreiben Project-Zuordnungen.  
  
## <a name="options"></a>Optionen  
**Quelltyp**  
Wählen Sie den Quelltyp für die Daten zuordnen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  
  
Wenn der Datentyp mit variabler Länge ist, erscheint die folgenden Felder unter **Quelltyp**:  
  
**From**  
Geben Sie die minimale Länge für diese Zuordnung. Z. B. für die **Nchar** -Datentyp, Sie können eingeben, 10, um anzugeben, dass diese Zuordnung für einen Bereich ab **nchar(10)** .  
  
**Aktion**  
Geben Sie die maximale Länge für diese Zuordnung. Z. B. für die **Nchar** -Datentyp, Sie können eingeben, 20, um anzugeben, dass diese Zuordnung für einen Bereich endet **nchar(20)** .  
  
**Zieltyp**  
Wählen Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp, der der Quelldatentyp zugeordnet ist. Wenn SSMA erstellt, die Tabelle oder eine gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ändert sich der Quelldatentyp auf diesen Datentyp.  
  
Wenn der Datentyp mit variabler Länge ist, erscheint das folgende Feld unter **Zieltyp**:  
  
**Replace with**  
Geben Sie die Ziellänge für diese Zuordnung. Z. B. für die **Nvarchar** -Datentyp, Sie können eingeben, 20, um anzugeben, dass die angegebene Quelle-Datentyp zugeordnet werden soll **nvarchar(20)** .  
  
