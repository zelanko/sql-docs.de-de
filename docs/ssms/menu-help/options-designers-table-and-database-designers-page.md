---
title: Optionen (Designer – Seite „Tabellen- und Datenbank-Designer“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Designers.Table_Designer
ms.assetid: b43f4b97-17b9-4004-a824-f77b9e145741
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b6c9bf93c92bb7797f179e0b6647993dff71e6b7
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105122"
---
# <a name="options-designers---table-and-database-designers-page"></a>Optionen (Designer – Seite „Tabellen- und Datenbank-Designer“)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Auf dieser Seite können Sie das Standardverhalten des Designers bestimmen. Um auf die Einstellungen zuzugreifen, klicken Sie im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Designer** , und klicken Sie dann auf **Tabellen-Designer**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
**Timeoutwert für Verbindungszeichenfolge für Tabellen-Designer-Updates überschreiben**  
Lässt zu, dass für die Aktionen des Tabellen-Designers ein neuer Timeoutwert festgelegt wird. Das kann hilfreich sein, wenn der Tabellen-Designer Auswirkungen auf eine große Tabelle hat und für die Änderung der Tabelle zusätzliche Zeit benötigt.  
  
**Transaktionstimeout nach**  
Legt einen Timeoutwert für den Tabellen-Designer fest.  
  
**Automatisches Erstellen von Änderungsskripts**  
Erstellt automatisch ein Skript für die Implementierung der im Tabellen-Designer definierten Änderungen.  
  
**Warnung bei Nullprimärschlüsseln**  
Stellt ein Warndialogfeld bereit, wenn ein für einen Primärschlüssel ausgewähltes Feld Nullwerte enthalten kann.  
  
**Warnung bei Unterschiederkennung**  
Wenn Sie dieses Kontrollkästchen aktivieren, werden beim Speichern der Änderungen in einem Nachrichtenfeld alle Überschneidungen zwischen Ihren Änderungen und den von einem anderen Benutzer vorgenommenen Änderungen aufgelistet.  
  
**Warnung bei betroffenen Tabellen**  
Stellt ein Warndialogfeld bereit, in dem die von der Aktion betroffenen Tabellen aufgeführt sind und zur Bestätigung aufgefordert wird.  
  
**Speichern von Änderungen verhindern, die die Neuerstellung der Tabelle erfordern**  
Verhindert, dass ein Benutzer Änderungen vornimmt, die eine Neuerstellung der Tabelle erfordern. Die folgenden Aktionen können die erneute Erstellung einer Tabelle erfordern:  
  
-   Hinzufügen einer neuen Spalte zur Mitte der Tabelle  
  
-   Löschen einer Spalte  
  
-   Ändern der NULL-Zulässigkeit einer Spalte  
  
-   Ändern der Reihenfolge der Spalten  
  
-   Ändern des Datentyps einer Spalte  
  
**Standardtabellenansicht**  
Wählen Sie aus, wie Tabellen in den Designern angezeigt werden sollen:  
  
-   **Standard**  
  
    Zeigt den Tabellenkopf, alle Spaltennamen, Datentypen und die Einstellung NULL-Werte zulassen an.  
  
-   **Spaltennamen**  
  
    Zeigt die Spaltennamen an.  
  
-   **Key**  
  
    Zeigt den Tabellenkopf und die Primärschlüsselspalten an.  
  
-   **Nur Name**  
  
    Zeigt nur den Tabellenkopf mit seinem Namen an.  
  
-   **Benutzerdefiniert**  
  
    Ermöglicht Ihnen die Auswahl der anzuzeigenden Spalten.  
  
**Tabellendialogfeld hinzufügen bei Neues Diagramm starten**  
Öffnet beim Öffnen der Designer automatisch das Dialogfeld **Tabelle hinzufügen** .  
  
