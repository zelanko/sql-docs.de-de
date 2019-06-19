---
title: DBMS-basierten Treibern | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc35f7bceff2d9e92b70448040bb602117b76c84
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63186308"
---
# <a name="dbms-based-drivers"></a>DBMS-basierte Treiber
DBMS-basierten Treibern werden mit Datenquellen wie z. B. Oracle- oder SQL Server verwendet, die eine eigenständige Datenbank-Engine für den Treiber mit bereitstellen. Diese Treiber Zugriff auf die physischen Daten über die eigenständigen-Engine; d. h. sie SQL-Anweisungen zum Senden und Abrufen der Ergebnisse von der Engine.  
  
 Da die DBMS-basierten Treibern auf eine vorhandenen Datenbank-Engine verwenden, sind sie in der Regel einfacher, als dateibasierten Treibern zu schreiben. Obwohl eine DBMS-basierten Treibers ganz einfach durch die Übersetzung von ODBC-Aufrufe in systemeigene API-Aufrufe implementiert werden kann, führt dies in einem langsameren-Treiber. Das zugrunde liegende Data Stream-Protokoll verwenden, das in der Regel ist der Funktionsweise der systemeigenen API ist eine bessere Möglichkeit, einen DBMS-basierten Treiber implementiert werden. Beispielsweise sollten ein SQL Server-Treiber TDS (die Daten streamen Protokoll für SQL Server) verwenden, anstatt der DB-Library (die systemeigene API für SQL Server). Eine Ausnahme von dieser Regel ist, wenn es sich bei ODBC die systemeigene API handelt. Watcom SQL ist beispielsweise eine eigenständige-Engine, die auf dem gleichen Computer wie die Anwendung befindet sich direkt als der Treiber geladen wird.  
  
 DBMS-basierten Treibern fungieren als Clients in einer Client-/Server-Konfiguration, in dem die Datenquelle als Server fungiert. In den meisten Fällen befinden sich die Client (Treiber) und Server (Datenquelle) auf verschiedenen Computern zwar sowohl auf dem gleichen Computer unter einem Multitasking-Betriebssystem befinden können. Eine dritte Möglichkeit ist eine *Gateway* die befindet sich zwischen dem Treiber und der Datenquelle. Ein Gateway ist eine Softwarekomponente, die bewirkt, dass ein DBMS an, wie eine andere aus. Zum Verwenden von SQL Server geschriebene Anwendungen können z. B. auch DB2-Daten über das Micro Decisionware DB2-Gateway zugreifen. Dieses Produkt führt DB2, wie SQL Server zu suchen.  
  
 Die folgende Abbildung zeigt drei verschiedene Konfigurationen von DBMS-basierten Treibern. In der ersten Konfiguration befinden sich in der Treiber und die Datenquelle auf demselben Computer. Im zweiten Fall befinden sich in der Treiber und die Datenquelle auf unterschiedlichen Computern. Im dritten die Treiber und die Datenquellensicht, die auf verschiedenen Computern befinden sich, und ein Gateway befindet sich zwischen ihnen, die sich auf noch einem anderen Computer befinden.  
  
 ![Drei Konfigurationen von DBMS&#45;basierte Treiber](../../odbc/reference/media/pr07.gif "pr07")
