---
title: Konfigurieren des ODBC-Treibers für Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- configuring ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], configuring
ms.assetid: 0a5f827c-0b80-4627-85cb-f10292b9fb33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bbdbe36ed9e6f254e2b738479698bd9eece09f8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281370"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Konfigurieren des ODBC-Treibers für Oracle
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Sie können die Leistung des ODBC-Treibers für Oracle steuern, indem Sie die Datenumgebung kennen und die Parameter der Datenquellenverbindung über das Dialogfeld [ODBC Data Source Administrator](../../odbc/admin/odbc-data-source-administrator.md) oder über Verbindungszeichenfolgenparameter korrekt festlegen. Das Dialogfeld enthält die folgenden Steuerelemente zum Herstellen einer Verbindung mit einer Datenquelle über das Dialogfeld oder mithilfe von Verbindungszeichenfolgen:  
  
-   **Registerkarte Benutzer DSN** Listet die Datenquellennamen auf, die lokal auf dem Computer sind.  
  
-   **Registerkarte System DSN** Ermöglicht das Hinzufügen oder Entfernen einer Systemdatenquelle. Auf Systemdatenquellen können alle Benutzer auf dem lokalen Computer zugreifen.  
  
-   **Datei-DSN-Registerkarte** Ermöglicht das Hinzufügen oder Entfernen einer Dateidatenquelle vom lokalen Computer. Dateidatenquellen können von allen Benutzern gemeinsam genutzt werden, für die derselbe Treiber installiert ist.  
  
-   **Registerkarte Treiber** Listet die installierten ODBC-Treiber auf.  
  
-   **Registerkarte Tracing** Hier können Sie angeben, wie der ODBC-Treiber-Manager Aufrufe von ODBC-Funktionen nachverfolgt. Sie können die Ablaufverfolgung für jede installierte ODBC-Anwendung separat konfigurieren.  
  
-   **Registerkarte "Verbindungspooling"** Ermöglicht die Auswahl der Verbindungsoptionen für jeden installierten Treiber.  
  
-   **Über Tab** Listet die installierten ODBC-Komponentendateien auf.  
  
 Nachdem Sie eine Datenquelle hinzugefügt haben, können Sie das Dialogfeld **ODBC-Datenquellenadministrator** verwenden, um den Zugriff auf ihre Datenquelle zu konfigurieren. Wählen Sie eine Datenquelle aus, und klicken Sie dann auf eine der Registerkarten, um die Informationen zu bearbeiten oder zu überprüfen.
