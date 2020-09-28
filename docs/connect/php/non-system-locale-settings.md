---
title: Nicht vom System festgelegte Gebietsschemaeinstellungen
description: Erfahren Sie, wie sich unterschiedliche Gebietsschemaeinstellungen in Linux und macOS auf die Microsoft-Treiber für PHP für SQL Server auswirken.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- locale, linux, macOS, system
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 303037729164d4165fc106529a901b58d4d049f4
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680525"
---
# <a name="non-system-locale-settings"></a>Nicht vom System festgelegte Gebietsschemaeinstellungen
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Dieser Abschnitt gilt nur für Linux- und macOS-Benutzer, insbesondere für diejenigen, die in ihren php-Anwendungen mit mehreren Gebietsschemas arbeiten.

Standardmäßig verwendet [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] die im System definierte Umgebungsvariable `LC_ALL` und überschreibt alle anderen `LC_xxx`-Kategorien (außer vielleicht `$LANG` oder `$LANGUAGE` unter bestimmten Umständen), was sich auf das Tausender-Trennzeichen, das Dezimalzeichen, den Zeichensatz, die Monats- und Tagesnamen, Anwendungsmeldungen wie Fehlermeldungen, das Währungssymbol usw. auswirkt.

Ab Version 5.8.0 können Benutzer die Lokalisierungseinstellungen mithilfe der Datei „php.ini“ konfigurieren, wie in den folgenden Beispielen gezeigt.

## <a name="set-locale-info-using-the-sqlsrv-driver"></a>Festlegen von Gebietsschemainformationen mithilfe des Treibers SQLSRV  
Fügen Sie am Ende der Datei „php.ini“ Folgendes ein:
  
```  
[sqlsrv]  
sqlsrv.SetLocaleInfo = <option>
```  
  
## <a name="set-locale-info-using-the-pdo_sqlsrv-driver"></a>Festlegen des Gebietsschemas mithilfe des Treibers PDO_SQLSRV  
Fügen Sie am Ende der Datei „php.ini“ Folgendes ein:
  
```  
[pdo_sqlsrv]  
pdo_sqlsrv.set_locale_info = <option>
```  
  
Für **option** ist einer der folgenden Werte möglich:  
  
|Option|Beschreibung des Verhaltens|
|---------|---------------|
|0|Der Treiber ignoriert die Gebietsschemaeinstellungen des Systems.|
|1|Der Treiber liest die Variable LC_CTYPE.|
|2|Der Treiber liest die Variable LC_ALL (Standardeinstellung).|
  

Die Kategorie `LC_CTYPE` legt Regeln für die Zeichenbehandlung fest, die die Interpretation der Sequenzen von Bytes von Textdatenzeichen, die Klassifizierung von Zeichen und das Verhalten von Zeichenklassen regeln. Sie steuert das Erkennen von Groß- und Kleinbuchstaben, alphabetischen und nicht alphabetischen Zeichen usw.

### <a name="explanation"></a>Erklärung

1. Option 0: Verwenden Sie diese Option, wenn Sie das Gebietsschema der Anwendung nicht ändern möchten.

1. Option 1: Verwenden Sie diese Option, um nur den Systemwert von `LC_CTYPE` festzulegen, ohne die anderen `LC_xxx`-Kategorien zu beeinflussen.

1. Option 2: Verwenden Sie `LC_ALL`, um alle `LC_xxx`-Kategorien zu überschreiben, was sich auf die php-Anwendung und ihre Erweiterungen auswirkt.

Wenn das Gebietsschema für ein php-Skript nicht mit dem des Systems übereinstimmt, müssen Sie möglicherweise das Gebietsschema in den php-Skripts angeben, indem Sie die in php integrierte Funktion [setlocale](https://www.php.net/manual/en/function.setlocale.php) aufrufen. 

Wenn die Standardeinstellung des Systems z. B. `en_US.UTF-8` ist, das php-Skript aber `de_DE.UTF-8` verwendet, rufen Sie die php-Funktion `setlocale()` entsprechend auf.

Geben Sie für die Option 2 nur dann das gewünschte Gebietsschema in Ihren php-Skripts an, wenn es sich von der Variablen `LC_ALL` unterscheidet.

> [!NOTE]
> Wenn in „php.ini“ nichts definiert ist, ist die aktuelle Standardeinstellung, alle anderen auf `LC_ALL` basierenden Gebietsschemaeinstellungen zu überschreiben, was als **veraltet** gilt. In naher Zukunft werden die Systemeinstellungen des Gebietsschemas standardmäßig ignoriert. Daher müssen Benutzer die Datei „php. ini“ entsprechend ändern, wenn Sie das aktuelle Verhalten beibehalten möchten.

Wenn die beiden Treiber SQLSRV und PDO_SQLSRV aktiviert sind, wird nicht empfohlen, unterschiedliche Optionen für die beiden Treiber festzulegen.
