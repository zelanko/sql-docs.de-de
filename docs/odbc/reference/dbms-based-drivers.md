---
title: DBMS-basierte Treiber | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306486"
---
# <a name="dbms-based-drivers"></a>DBMS-basierte Treiber
DBMS-basierte Treiber werden mit Datenquellen wie Oracle oder SQL Server verwendet, die eine eigenständige Datenbank-Engine für den Treiber bereitstellen. Diese Treiber greifen über den eigenständigen Motor auf die physischen Daten zu. Das heißt, sie senden SQL-Anweisungen an das Modul und rufen Ergebnisse ab.  
  
 Da DBMS-basierte Treiber ein vorhandenes Datenbankmodul verwenden, sind sie in der Regel einfacher zu schreiben als dateibasierte Treiber. Obwohl ein DBMS-basierter Treiber einfach durch Übersetzen von ODBC-Aufrufen in systemeigene API-Aufrufe implementiert werden kann, führt dies zu einem langsameren Treiber. Eine bessere Möglichkeit zum Implementieren eines DBMS-basierten Treibers besteht darin, das zugrunde liegende Datenstromprotokoll zu verwenden, was in der Regel die systemeigene API tut. Beispielsweise sollte ein SQL Server-Treiber TDS (das Datenstromprotokoll für SQL Server) anstelle der DB Library (die systemeigene API für SQL Server) verwenden. Eine Ausnahme von dieser Regel ist, wenn ODBC die systemeigene API ist. Watcom SQL ist z. B. ein eigenständiges Modul, das sich auf demselben Computer wie die Anwendung befindet und direkt als Treiber geladen wird.  
  
 DBMS-basierte Treiber fungieren als Client in einer Client/Server-Konfiguration, bei der die Datenquelle als Server fungiert. In den meisten Fällen befinden sich Client (Treiber) und Server (Datenquelle) auf verschiedenen Computern, obwohl sich beide auf demselben Computer befinden können, auf dem ein Multitasking-Betriebssystem ausgeführt wird. Eine dritte Möglichkeit ist ein *Gateway,* das zwischen Treiber und Datenquelle sitzt. Ein Gateway ist eine Software, die bewirkt, dass ein DBMS wie ein anderes aussieht. Beispielsweise können Anwendungen, die für die Verwendung von SQL Server geschrieben wurden, auch über das Micro Decisionware DB2 Gateway auf DB2-Daten zugreifen. Dieses Produkt bewirkt, dass DB2 wie SQL Server aussieht.  
  
 Die folgende Abbildung zeigt drei verschiedene Konfigurationen von DBMS-basierten Treibern. In der ersten Konfiguration befinden sich Treiber und Datenquelle auf demselben Computer. In der zweiten befinden sich der Treiber und die Datenquelle auf verschiedenen Computern. In der dritten befinden sich der Treiber und die Datenquelle auf verschiedenen Computern, und ein Gateway befindet sich zwischen ihnen und befindet sich auf einem anderen Computer.  
  
 ![Drei Konfigurationen für DBMS-&#45;-basierte Treiber](../../odbc/reference/media/pr07.gif "pr07")
