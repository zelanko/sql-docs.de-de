---
title: Konfigurieren den ODBC-Treiber für Oracle | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096679"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Konfigurieren des ODBC-Treibers für Oracle
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Sie können die Leistung des ODBC-Treibers für Oracle steuern, indem Sie die Data-Umgebung und ordnungsgemäß Festlegen der Parameter für die datenquellenverbindung über die [ODBC-Datenquellenadministrator](../../odbc/admin/odbc-data-source-administrator.md) Dialogfeld ein, oder über eine Verbindung herstellen Zeichenfolgenparameter. Das Dialogfeld bietet die folgenden Steuerelemente für die Verbindung mit einer Datenquelle mithilfe des Dialogfelds aus, oder schließen Sie Zeichenfolgen mit:  
  
-   **Registerkarte "Benutzer-DSN"** führt den Datenquellennamen, die sich lokal auf dem Computer befinden.  
  
-   **Registerkarte "System-DSN"** ermöglicht es Ihnen, hinzufügen oder entfernen eine Systemdatenquelle. System-Datenquellen können von allen Benutzern auf dem lokalen Computer zugegriffen werden.  
  
-   **Registerkarte "Datei-DSN"** ermöglicht es Ihnen, hinzufügen oder entfernen eine Datenquelle aus dem lokalen Computer. Dateidatenquellen können alle Benutzer freigegeben werden, die die gleichen Treiber installiert haben.  
  
-   **Registerkarte "Treiber"** installierten ODBC-Treiber enthält.  
  
-   **Ablaufverfolgung Registerkarte** können Sie angeben, wie der ODBC-Treiber-Manager für Aufrufe von Funktionen der ODBC-ablaufverfolgungen. Sie können die Ablaufverfolgung für jeden installierten ODBC-Anwendung getrennt konfigurieren.  
  
-   **Registerkarte "Verbindungs-Pooling"** können Sie Verbindungsoptionen für jeden installierten Treiber auswählen.  
  
-   **Zur Registerkarte** Listet die Dateien der installierten ODBC-Komponenten.  
  
 Nachdem Sie eine Datenquelle hinzugefügt haben, können Sie die **ODBC-Datenquellenadministrator** Dialogfeld so konfigurieren Sie den Zugriff auf die Datenquelle. Wählen Sie eine Datenquelle aus, und klicken Sie dann auf eine der Registerkarten bearbeiten, oder überprüfen die Informationen.
