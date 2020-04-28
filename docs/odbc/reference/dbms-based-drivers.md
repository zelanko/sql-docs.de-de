---
title: DBMS-basierte Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drivers [ODBC], DBMS-based drivers
- DBMS-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
ms.assetid: e2208ee0-4cd6-4f0d-bb71-a0b54f7d9330
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e7b7b153d0b0cb0a3e6a3d738908b0039b95679
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306486"
---
# <a name="dbms-based-drivers"></a>DBMS-basierte Treiber
DBMS-basierte Treiber werden mit Datenquellen wie Oracle oder SQL Server verwendet, die eine eigenständige Datenbank-Engine bereitstellen, die vom Treiber verwendet werden soll. Diese Treiber greifen über die eigenständige Engine auf die physischen Daten zu. Das heißt, dass Sie SQL-Anweisungen an senden und Ergebnisse aus der Engine abrufen.  
  
 Da DBMS-basierte Treiber eine vorhandene Datenbank-Engine verwenden, sind Sie in der Regel einfacher zu schreiben als dateibasierte Treiber. Obwohl ein DBMS-basierter Treiber leicht durch die Übersetzung von ODBC-Aufrufen an Native API-Aufrufe implementiert werden kann, führt dies zu einem langsameren Treiber. Eine bessere Möglichkeit zum Implementieren eines DBMS-basierten Treibers besteht darin, das zugrunde liegende Datenstrom Protokoll zu verwenden. Dies ist in der Regel das, was die Native API tut. Beispielsweise sollte ein SQL Server Treiber TDS (das Datenstrom Protokoll für SQL Server) anstelle der DB-Bibliothek (die Native API für SQL Server) verwenden. Eine Ausnahme von dieser Regel ist, wenn ODBC die Native API ist. Beispielsweise ist Watcom SQL eine eigenständige Engine, die sich auf demselben Computer wie die Anwendung befindet und direkt als Treiber geladen wird.  
  
 DBMS-basierte Treiber fungieren als Client in einer Client-/Serverkonfiguration, bei der die Datenquelle als Server fungiert. In den meisten Fällen befinden sich der Client (Treiber) und der Server (Datenquelle) auf unterschiedlichen Computern, obwohl sich beide auf demselben Computer befinden könnten, auf dem ein Multitasking-Betriebssystem ausgeführt wird. Eine dritte Möglichkeit ist ein *Gateway,* das sich zwischen dem Treiber und der Datenquelle befindet. Ein Gateway ist eine Software, die bewirkt, dass ein DBMS wie ein anderes aussieht. Beispielsweise können Anwendungen, die für die Verwendung von SQL Server geschrieben wurden, auch über das Micro DecisionWare DB2-Gateway auf DB2-Daten zugreifen. Dieses Produkt bewirkt, dass DB2 wie SQL Server aussieht.  
  
 Die folgende Abbildung zeigt drei verschiedene Konfigurationen von DBMS-basierten Treibern. In der ersten Konfiguration befinden sich der Treiber und die Datenquelle auf demselben Computer. Im zweiten Bereich befinden sich der Treiber und die Datenquelle auf unterschiedlichen Computern. Im dritten befinden sich der Treiber und die Datenquelle auf unterschiedlichen Computern, und ein Gateway befindet sich auf einem anderen Computer.  
  
 ![Drei Konfigurationen für DBMS-&#45;basierte Treiber](../../odbc/reference/media/pr07.gif "pr07")
