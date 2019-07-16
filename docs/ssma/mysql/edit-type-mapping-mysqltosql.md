---
title: Bearbeiten der Typzuordnung (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 184f7ab2-725f-491e-a15b-b889f2fb6a68
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d31304dae7246e425ef54af6d1382af7e885696c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103000"
---
# <a name="edit-type-mapping-mysqltosql"></a>Bearbeiten der Typzuordnung (MySqlToSql)
Die **Bearbeiten der Typzuordnung** Dialogfeld können Sie angeben, wie Datentypen zwischen Quelle und Ziel-Datenbankobjekten zugeordnet werden.  
  
Sie können dieses Dialogfeld an mehreren Stellen zugreifen:  
  
-   Bei Auswahl einer Quelldatenbank oder ein Datenbankobjekt, das **Type Mapping** Registerkarte wird rechts neben dem Metadaten-Explorer angezeigt. Klicken Sie auf **hinzufügen** fügen Sie eine neue Zuordnung hinzu, oder klicken Sie auf **bearbeiten** so ändern Sie eine vorhandene Typzuordnung.  
  
-   Auf der **Tools** , wählen Sie im Menü **Projekteinstellungen** oder **Projekt Standardeinstellungen**. Wählen Sie im daraufhin angezeigten Dialogfeld **Type Mapping**. Klicken Sie auf **hinzufügen** fügen Sie eine neue Zuordnung hinzu, oder klicken Sie auf **bearbeiten** so ändern Sie eine vorhandene Typzuordnung.  
  
-   Tabelle-spezifische Zuordnungen für Projekte replikationsdatentyp-Zuordnungen und Datenbank zu überschreiben. Datenbank-spezifische Zuordnungen überschreiben Project-Zuordnungen.  
  
## <a name="options"></a>Optionen  
  
##### <a name="source-type"></a>Quelltyp  
Wählen Sie den Quelltyp für die Daten in einen SQL Server-Datentyp zugeordnet.  
  
Wenn der Datentyp mit variabler Länge ist, erscheint die folgenden Felder unter **Sourcetype**:  
  
##### <a name="from"></a>Von  
Geben Sie die minimale Länge für diese Zuordnung. Z. B. für die **Nchar** -Datentyp, Sie können eingeben, 10, um anzugeben, dass diese Zuordnung für einen Bereich ab **nchar(10).**  
  
##### <a name="to"></a>Beschreibung  
Geben Sie die maximale Länge für diese Zuordnung. Z. B. für die **Nchar** -Datentyp, Sie können eingeben, 20, um anzugeben, dass diese Zuordnung für einen Bereich endet **nchar(20).**  
  
##### <a name="target-type"></a>Zieltyp  
Wählen Sie die SQL Server-Datentyp, der der Datentyp der Quelle zugeordnet ist. Wenn SSMA die Tabelle erstellt oder in der SQL Server vorhanden ist, ändert sich der Quelldatentyp auf diesen Datentyp.  
  
Wenn der Datentyp mit variabler Länge ist, erscheint das folgende Feld unter **Zieltyp**:  
  
##### <a name="replace-with"></a>Ersetzen durch  
Geben Sie die Ziellänge für diese Zuordnung. Z. B. für die **Nvarchar** -Datentyp, Sie können eingeben, 20, um anzugeben, dass die angegebene Quelle-Datentyp zugeordnet werden soll **Nvarchar (20).**  
  
