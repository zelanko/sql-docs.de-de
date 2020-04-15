---
title: ODBC-Architektur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07435dc1a5fbe800f2260e914f315cfe93dd8d1b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305131"
---
# <a name="odbc-architecture"></a>ODBC-Architektur
Die ODBC-Architektur besteht aus vier Komponenten:  
  
-   **Anwendung** Führt die Verarbeitung aus und ruft ODBC-Funktionen auf, um SQL-Anweisungen zu übermitteln und Ergebnisse abzurufen.  
  
-   **Treiber-Manager** Lädt und entlädt Treiber im Auftrag einer Anwendung. Verarbeitet ODBC-Funktionen, die aufrufe oder an einen Treiber weiterleitet.  
  
-   **Treiber** Verarbeitet ODBC-Funktionsaufrufe, sendet SQL-Anforderungen an eine bestimmte Datenquelle und gibt Ergebnisse an die Anwendung zurück. Bei Bedarf ändert der Treiber die Anforderung einer Anwendung, sodass die Anforderung der Syntax entspricht, die vom zugeordneten DBMS unterstützt wird.  
  
-   **Datenquelle** Besteht aus den Daten, auf die der Benutzer zugreifen möchte, und dem zugehörigen Betriebssystem, DBMS und der Netzwerkplattform (falls vorhanden), die für den Zugriff auf das DBMS verwendet werden.  
  
 Beachten Sie die folgenden Punkte zur ODBC-Architektur. Zunächst können mehrere Treiber und Datenquellen vorhanden sein, wodurch die Anwendung gleichzeitig auf Daten aus mehr als einer Datenquelle zugreifen kann. Zweitens wird die ODBC-API an zwei Stellen verwendet: zwischen der Anwendung und dem Treiber-Manager sowie zwischen dem Treiber-Manager und jedem Treiber. Die Schnittstelle zwischen dem Treiber-Manager und den Treibern wird manchmal als *Dienstanbieterschnittstelle* oder *SPI*bezeichnet. Bei ODBC sind die API (Application Programming Interface) und die Service Provider Interface (SPI) identisch. das heißt, der Treiber-Manager und jeder Treiber haben die gleiche Schnittstelle zu den gleichen Funktionen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Anwendungen](../../odbc/reference/applications.md)  
  
-   [Der Treiber-Manager](../../odbc/reference/the-driver-manager.md)  
  
-   [Treiber](../../odbc/reference/drivers.md)  
  
-   [Datenquellen](../../odbc/reference/data-sources.md)
