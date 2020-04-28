---
title: Bewertungsbericht (oracledesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 168b7465-a6d6-4329-b46e-fc6c5a3f2d9d
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 75fdb97b5b7d763694289d762edc65b4536a86c3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68264523"
---
# <a name="assessment-report-oracletosql"></a>Bewertungsbericht (OracleToSQL)
Im Fenster Bewertungsbericht werden die Ergebnisse der Konvertierung von Datenbankobjekten in [!INCLUDE[tsql](../../includes/tsql-md.md)] die-Syntax angezeigt. Außerdem können Sie die Komplexität und die Kosten ihrer Migrationsprojekte schätzen.  
  
Um auf den Bewertungsbericht zuzugreifen, wählen Sie im quellmetadatenexplorer zu konvertierende Objekte aus, klicken Sie mit der rechten Maustaste auf **Schemas** oder **Synonyme**, und wählen Sie dann **Bericht erstellen**  
  
## <a name="options"></a>Optionen  
  
|||  
|-|-|  
|Begriff|Definition|  
|**Konvertierungs Statistik**|Zeigt die Konvertierungs Statistik nach Anweisungs Typ an. Dieser Bereich ist sichtbar, wenn im linken Bereich ein Gruppen Objekt, z. b. ein Schema, oder ein Objekt ohne Code ausgewählt wird.|  
|**Objekte nach Kategorien**|Zeigt die Anzahl der Objekte nach Kategorie an. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein Gruppen Objekt, z. b. ein Schema, oder ein Objekt ohne Code ausgewählt ist.|  
|**Statistik**|Zeigt die Konvertierungsstatistiken für das ausgewählte Objekt an. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist. Sie müssen möglicherweise **Statistiken**erweitern, die sich direkt oberhalb des **Quell** Bereichs befinden, um diesen Bereich anzuzeigen.|  
|**Quelle**|Zeigt den Oracle-Code für das ausgewählte Objekt an und hebt Code hervor, der nicht [!INCLUDE[tsql](../../includes/tsql-md.md)]in konvertiert wurde. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist.<br /><br />Klicken Sie zum Festlegen oder Löschen von Lesezeichen auf die Zeilennummern. Verwenden Sie die Schaltflächen am oberen Rand des Fensters, um durch den Code zu navigieren.|  
|**Ziel**|Zeigt den resultierenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Code der Konvertierung für das ausgewählte Objekt und Fehlermeldungen für Code an, der nicht konvertiert wurde. Dieser Bereich ist nur sichtbar, wenn im linken Bereich ein einzelnes Objekt mit Code ausgewählt ist.<br /><br />Klicken Sie zum Festlegen oder Löschen von Lesezeichen auf die Zeilennummern. Verwenden Sie die Schaltflächen am oberen Rand des Fensters, um durch den Code zu navigieren.|  
|**Meldungsbereich**|Zeigt die Fehler, Warnungen und Informationsmeldungen an, die beim Erstellen des Bewertungsberichts generiert wurden. Nachrichten werden nach Zahl gruppiert. Um den Code anzuzeigen, der den Fehler verursacht hat, klicken Sie auf **Fehler**, **Warnungen**oder **Info**, erweitern Sie die Kategorie der Meldungen, und klicken Sie dann auf eine Meldung.|  
  
