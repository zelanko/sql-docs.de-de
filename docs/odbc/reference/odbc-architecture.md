---
title: ODBC-Architektur | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83e35d58d180336c349e83c7991d27f7007aca4e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752848"
---
# <a name="odbc-architecture"></a>ODBC-Architektur
Die ODBC-Architektur besteht aus vier Komponenten:  
  
-   **Anwendung** Verarbeitung und ruft ODBC-Funktionen zum Übermitteln von SQL-Anweisungen und Abrufen von Ergebnissen führt.  
  
-   **Treiber-Manager** laden und Entladen von Treibern für eine Anwendung. Prozesse ODBC-Funktion aufruft, oder übergibt sie an einen Treiber.  
  
-   **Treiber** Prozesse ODBC-Funktion aufruft, sendet SQL-Anforderungen an eine bestimmte Datenquelle und gibt Ergebnisse an die Anwendung zurück. Bei Bedarf ändert der Treiber die Anforderung einer Anwendung, sodass die Anforderung von der zugeordneten DBMS unterstützte Syntax entspricht.  
  
-   **Datenquelle** besteht aus den Daten der Benutzer möchte den Zugriff und die zugehörigen Betriebssystem, DBMS und Netzwerkplattform (sofern vorhanden) verwendet wird, um das DBMS zugreifen.  
  
 Beachten Sie die folgenden Punkte bezüglich der ODBC-Architektur. Erste, mehrere Treibern und Datenquellen können vorhanden sein, wodurch die Anwendung gleichzeitig auf Daten aus mehr als eine Datenquelle zugreifen. Zweitens wird der ODBC-API verwendet, an zwei Orten: zwischen der Anwendung und der Treiber-Manager sowie zwischen der Treiber-Manager und jeden Treiber. Die Schnittstelle zwischen der Treiber-Manager und der Treiber wird manchmal als bezeichnet die *Service Provider Interface* oder *SPI*. Für ODBC Application programming Interface, (API) und die Service Provider Interface (SPI) sind identisch. der Treiber-Manager, und jeder Treiber verfügen, also die gleiche Schnittstelle für die gleichen Funktionen auf.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Anwendungen](../../odbc/reference/applications.md)  
  
-   [Der Treiber-Manager](../../odbc/reference/the-driver-manager.md)  
  
-   [Treiber](../../odbc/reference/drivers.md)  
  
-   [Datenquellen](../../odbc/reference/data-sources.md)
