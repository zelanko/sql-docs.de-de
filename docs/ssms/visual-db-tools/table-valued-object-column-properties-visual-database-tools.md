---
description: Tabellenwertobjekt (Spalte) Eigenschaften (Visual Database Tools)
title: Tabellenwertobjekt (Spalte) Eigenschaften
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.QueryViewColumn
ms.assetid: 212d9bcd-aded-4313-a6b9-d7e2270e5954
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: f33c6df2e1acfa5c014b6739acd61c4d0153631c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88312706"
---
# <a name="table-valued-object-column-properties-visual-database-tools"></a>Tabellenwertobjekt (Spalte) Eigenschaften (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
 Diese Eigenschaften erscheinen, wenn Sie im Abfrage- und Sicht-Designer im Bereich **Diagramm** eine Spalte in einem Tabellenwertobjekt auswählen.  
  
> [!NOTE]  
> Die in diesem Thema behandelten Eigenschaften sind nicht alphabetisch, sondern nach Kategorie angeordnet.  
  
> [!NOTE]  
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern.  
  
**Kategorie Identität**  
Wird erweitert, um die Eigenschaft **Name** anzuzeigen.  
  
**Name**  
Zeigt den Namen der ausgewählten Spalte an.  
  
**Abfrage-Designer – Kategorie**  
Wird erweitert und zeigt die Eigenschaften für **NULL-Werte zulassen**, **Sortierung**, **Datentyp**, **Länge**, **Genauigkeit**, **Dezimalstellen**und **Größe**an.  
  
**NULL-Werte zulassen**  
Zeigt an, ob der Datentyp der Spalte NULL-Werte zulässt.  
  
**Sortierung**  
Zeigt die Sortierungseinstellung der ausgewählten Spalte an. Die Sortierung kann auf der Registerkarte Spalteneigenschaften des Tabellen-Designers festgelegt werden.  
  
**Datentyp**  
Zeigt den Datentyp der ausgewählten Spalte an.  
  
**Länge**  
Zeigt die Anzahl der Zeichen oder Stellen an, die der Datentyp der ausgewählten Spalte zulässt. Diese Eigenschaft ist nur für zeichenbasierte Datentypen verfügbar.  
  
> [!NOTE]  
> Die Größe in Byte wird darunter in der Eigenschaft **Größe** angezeigt.  
  
**Genauigkeit**  
Zeigt die maximale Anzahl der für numerische Datentypen zulässigen Stellen. Bei nicht numerischen Datentypen wird diese Eigenschaft mit **0** angegeben.  
  
**Skalierung**  
Zeigt die maximale Anzahl von Stellen an, die bei numerischen Datentypen rechts vom Dezimalkomma erscheinen können. Dieser Wert muss kleiner oder gleich der Genauigkeit sein. Bei nicht numerischen Datentypen wird diese Eigenschaft mit **0** angegeben.  
  
**Größe**  
Zeigt die für den Datentyp der Spalte zulässige Größe in Byte an. Beispiel: Ein nchar-Datentyp kann eine Länge von 10 besitzen (die Anzahl der Zeichen), wegen der Unicode-Zeichensätze aber eine Größe von 20 Byte besitzen.  
  
