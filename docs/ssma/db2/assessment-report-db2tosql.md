---
title: Bewertungsbericht (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e13eba0-e3cf-4205-974f-c00f982061de
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 017bb1a123c7465efd7ad895bb34fec8b87a707e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938307"
---
# <a name="assessment-report-db2tosql"></a>Bewertungsbericht (DB2ToSQL)
Im Fenster Bewertungsbericht werden die Ergebnisse der Konvertierung von Datenbankobjekten in [!INCLUDE[tsql](../../includes/tsql-md.md)] die-Syntax angezeigt. Außerdem können Sie die Komplexität und die Kosten ihrer Migrationsprojekte schätzen.  
  
Um auf den Bewertungsbericht zuzugreifen, wählen Sie im quellmetadatenexplorer zu konvertierende Objekte aus, klicken Sie mit der rechten Maustaste auf **Schemas** oder **Synonyme**, und wählen Sie dann **Bericht erstellen**  
  
## <a name="options"></a>Tastatur  
  
|||  
|-|-|  
|Begriff|Definition|  
|**Konvertierungs Statistik**|Zeigt die Konvertierungs Statistik nach Anweisungs Typ an. Dieser Bereich ist sichtbar, wenn im linken Bereich ein Gruppen Objekt, z. b. ein Schema, oder ein Objekt ohne Code ausgewählt wird.|  
|**Objekte nach Kategorien**|Zeigt die Anzahl der Objekte nach Kategorie an. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein Gruppen Objekt, z. b. ein Schema, oder ein Objekt ohne Code ausgewählt ist.|  
|**Statistik**|Zeigt die Konvertierungsstatistiken für das ausgewählte Objekt an. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist. Sie müssen möglicherweise **Statistiken**erweitern, die sich direkt oberhalb des **Quell** Bereichs befinden, um diesen Bereich anzuzeigen.|  
|**`Source`**|Zeigt den DB2-Code für das ausgewählte Objekt an und hebt Code hervor, der nicht [!INCLUDE[tsql](../../includes/tsql-md.md)]in konvertiert wurde. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist.<br /><br />Klicken Sie zum Festlegen oder Löschen von Lesezeichen auf die Zeilennummern. Verwenden Sie die Schaltflächen am oberen Rand des Fensters, um durch den Code zu navigieren.|  
|**Spar**|Zeigt den resultierenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Code der Konvertierung für das ausgewählte Objekt und Fehlermeldungen für Code an, der nicht konvertiert wurde. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist.<br /><br />Klicken Sie zum Festlegen oder Löschen von Lesezeichen auf die Zeilennummern. Verwenden Sie die Schaltflächen am oberen Rand des Fensters, um durch den Code zu navigieren.|  
|**Meldungsbereich**|Zeigt die Fehler, Warnungen und Informationsmeldungen an, die beim Erstellen des Bewertungsberichts generiert wurden. Nachrichten werden nach Zahl gruppiert. Um den Code anzuzeigen, der den Fehler verursacht hat, klicken Sie auf **Fehler**, **Warnungen**oder **Info**, erweitern Sie die Kategorie der Meldungen, und klicken Sie dann auf eine Meldung.|  
  
