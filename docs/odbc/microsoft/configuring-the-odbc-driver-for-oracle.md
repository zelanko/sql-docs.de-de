---
title: Konfigurieren des ODBC-Treibers für Oracle | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc163f53c9dc234702f6f74426eb65f57cec26b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096679"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Konfigurieren des ODBC-Treibers für Oracle
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Sie können die Leistung des ODBC-Treibers für Oracle steuern, indem Sie die Daten Umgebung kennen und die Parameter der Datenquellen Verbindung im Dialogfeld [ODBC-Datenquellen-Administrator](../../odbc/admin/odbc-data-source-administrator.md) oder mithilfe von Verbindungs Zeichenfolgen-Parametern ordnungsgemäß festlegen. Das Dialogfeld enthält die folgenden Steuerelemente für das Herstellen einer Verbindung mit einer Datenquelle mithilfe des Dialog Felds oder mithilfe von Verbindungs Zeichenfolgen:  
  
-   **Registerkarte Benutzer-DSN** Listet die Namen der Datenquellen auf, die sich lokal auf dem Computer befinden.  
  
-   **Registerkarte System-DSN** Ermöglicht das Hinzufügen oder Entfernen einer Systemdaten Quelle. Auf System Datenquellen kann von allen Benutzern auf dem lokalen Computer zugegriffen werden.  
  
-   **Registerkarte Datei-DSN** Ermöglicht das Hinzufügen oder Entfernen einer Datei Datenquelle auf dem lokalen Computer. Datei Datenquellen können von allen Benutzern gemeinsam genutzt werden, die den gleichen Treiber installiert haben.  
  
-   **Registerkarte Treiber** Listet die installierten ODBC-Treiber auf.  
  
-   **Registerkarte Ablauf Verfolgung** Hiermit können Sie angeben, wie der ODBC-Treiber-Manager Aufrufe von ODBC-Funktionen verfolgt. Sie können die Ablauf Verfolgung für jede installierte ODBC-Anwendung separat konfigurieren.  
  
-   **Registerkarte Verbindungs Pooling** Ermöglicht es Ihnen, Verbindungsoptionen für jeden installierten Treiber auszuwählen.  
  
-   Info- **Registerkarte** Listet die installierten ODBC-Komponenten Dateien auf.  
  
 Nachdem Sie eine Datenquelle hinzugefügt haben, können Sie das Dialogfeld **ODBC-Datenquellen-Administrator** verwenden, um den Zugriff auf die Datenquelle zu konfigurieren. Wählen Sie eine Datenquelle aus, und klicken Sie dann auf eine der Registerkarten, um die Informationen zu bearbeiten oder zu überprüfen.
