---
title: 'Schritt 1: Konfigurieren der Umgebung für PHP'
description: Schritt 1 dieses Leitfadens für die ersten Schritte umfasst die Installation von PHP, des Microsoft ODBC Driver for SQL Server und das Konfigurieren der Entwicklungsumgebung.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0bce6022-00bd-45c6-9671-eaa9dfa395a8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88eb2c2c67eac3ecd9fba2c79c143de28cf60d22
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633171"
---
# <a name="step-1-configure-environment-for-php-development"></a>Schritt 1: Konfigurieren der Umgebung für PHP-Entwicklung
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]




* Bestimmen Sie, welche Version des PHP-Treibers Sie basierend auf Ihrer Umgebung verwenden. Verwenden Sie dazu die folgenden Informationsressourcen:  [Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](system-requirements-for-the-php-sql-driver.md)
* Laden Sie den für Sie zutreffenden PHP-Treiber hier herunter, und installieren Sie ihn: [Download des Microsoft-PHP-Treibers](https://www.microsoft.com/download/details.aspx?id=20098)  
* Laden Sie den für Sie zutreffenden ODBC-Treiber hier herunter, und installieren Sie ihn:  [Herunterladen des ODBC-Treibers für SQL Server](../odbc/download-odbc-driver-for-sql-server.md)  
* Konfigurieren Sie den PHP-Treiber und den Webserver für Ihr spezifisches Betriebssystem:

### <a name="windows"></a>Windows  
  

* Konfigurieren und laden Sie den PHP-Treiber wie hier beschrieben: [Loading the Microsoft Drivers for PHP for SQL Server (Laden von Microsoft-Treibern für PHP für SQL Server)](../../connect/php/loading-the-php-sql-driver.md) 
* Konfigurieren Sie die IIS zum Hosten von PHP-Anwendungen wie hier beschrieben: [Konfigurieren der IIS für Microsoft-Treiber für PHP für SQL Server](../../connect/php/configuring-iis-for-php-sql-driver.md)

### <a name="linux-and-macos"></a>Linux und macOS


*   Konfigurieren Sie das Laden des PHP-Treibers und Ihren Webserver zum Hosten von PHP-Anwendungen wie hier beschrieben: [Tutorial zur Installation der PHP-Treiber unter Linux und macOS](../../connect/php/installation-tutorial-linux-mac.md)
