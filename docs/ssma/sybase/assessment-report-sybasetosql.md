---
description: Bewertungsbericht (SybaseToSQL)
title: Bewertungsbericht (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5bf7a2ac886165fa4228f78394065124a05bb67a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88372386"
---
# <a name="assessment-report-sybasetosql"></a>Bewertungsbericht (SybaseToSQL)
Im Fenster Bewertungsbericht werden die Ergebnisse der Konvertierung von Datenbankobjekten in die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax angezeigt. Außerdem können Sie die Komplexität und die Kosten ihrer Migrationsprojekte schätzen.  
  
Um auf den Bewertungsbericht zuzugreifen, wählen Sie im quellmetadatenexplorer zu konvertierende Objekte aus, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und wählen Sie dann **Bericht**  
  
## <a name="options"></a>Tastatur  
**Konvertierungs Statistik**  
Zeigt die Konvertierungs Statistik nach Anweisungs Typ an. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein Gruppen Objekt, z. b. ein Schema, oder ein Objekt ohne Code ausgewählt ist.  
  
**Objekte nach Kategorie**  
Zeigt die Konvertierungs Statistik nach Objekttyp an. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein Gruppen Objekt, z. b. ein Schema, oder ein Objekt ohne Code ausgewählt ist.  
  
**Statistik**  
Zeigt die Konvertierungsstatistiken für das ausgewählte Objekt an. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist. Möglicherweise müssen Sie **Statistiken** erweitern, um diesen Bereich anzuzeigen.  
  
**Quell Navigation**  
Zeigt den ASE-Code für das ausgewählte Objekt an und hebt Code hervor, der nicht in konvertiert wurde [!INCLUDE[tsql](../../includes/tsql-md.md)] . Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist.  
  
Klicken Sie zum Festlegen oder Löschen von Lesezeichen auf die Zeilennummern. Verwenden Sie die Schaltflächen am oberen Rand des Fensters, um durch den Code zu navigieren.  
  
**Ziel Navigation**  
Zeigt den resultierenden Code der Konvertierung [!INCLUDE[tsql](../../includes/tsql-md.md)] für das ausgewählte Objekt und Fehlermeldungen für Code an, der nicht konvertiert wurde. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist.  
  
Klicken Sie zum Festlegen oder Löschen von Lesezeichen auf die Zeilennummern. Verwenden Sie die Schaltflächen am oberen Rand des Fensters, um durch den Code zu navigieren.  
  
**Meldungsbereich**  
Zeigt die Fehler, Warnungen und Informationsmeldungen an, die beim Erstellen des Bewertungsberichts generiert werden. Nachrichten werden nach Zahl gruppiert. Um den Code anzuzeigen, der den Fehler verursacht hat, klicken Sie auf **Fehler**, **Warnung**oder **Info**, erweitern Sie die Kategorie der Meldungen, und klicken Sie dann auf eine Meldung.  
  
