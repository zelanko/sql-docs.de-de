---
title: Richtlinien und Einschränkungen von SQLXML 4,0 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
author: rothja
ms.author: jroth
ms.openlocfilehash: e020cbf0ac32e4c878b0b74b67e7c9c679d5d178
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015392"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a>Richtlinien und Einschränkungen von SQLXML 4.0
  Bei der Arbeit mit SQLXML 4.0 gilt Folgendes:  
  
-   Das als Abfrageergebnis zurückgegebene XML wird nicht anhand des Zuordnungsschemas, das das XML erstellt hat, überprüft.  
  
-   SQLXML 4.0 umfasst versionsunabhängige und versionsabhängige Programm-IDs. Es wird empfohlen, dass alle Produktionsanwendungen versionsabhängige Programm-IDs verwenden. Dies ist besonders wichtig, da SQLXML 4.0 nicht vollständig abwärtskompatibel ist. Die Verwendung von versionsabhängige Programm-IDs schützt vor möglichen Produktionsfehlern beim Installieren neuerer Versionen. Mit jeder neuen Version kann sich das Programmverhalten aus verschiedenen Gründen, z. B. aufgrund von Fehlerbehebungen, möglichen Designänderungen usw. ändern. Die Verwendung von versionsabhängigen Programm-IDs schützt vor unerwarteten Fehlern beim Installieren neuerer Versionen. Wenn Sie eine neuere Version installieren, arbeitet die Anwendung bei versionsabhängigen Programm-IDs weiterhin fehlerfrei. Wenn Sie die vorherigen versionsabhängigen Programm-IDs ändern und die aktuelle versionsabhängigen Programm-IDs in einer neueren Version verwenden, müssen Sie die Anwendung erst testen, bevor Sie die Arbeit damit aufnehmen. Anwendungen mit versionsunabhängigen Programm-IDs schlagen beispielsweise möglicherweise im folgenden Szenario fehl:  
  
     Sie führen eine Anwendung aus, die SQLXML 4.0 und versionsunabhängige Programm-IDs verwendet, und Sie installieren einige andere Softwareprogramme. Dabei könnte mit diesem Programm eine frühere Version von SQLXML installiert werden. Ihre Anwendung schlägt fehl, da die versionsunabhängigen Programm-IDs in der Anwendung nun auf die frühere Version von SQLXML verweisen, die nur bedingt über das SQLXML-Funktion verfügen, das Ihre Anwendung verwendet.  
  
-   Wenn Sie aus irgendeinem Grund den SQLXMLOLEDB-Anbieter nicht verwenden möchten und stattdessen den SQLOLEDB-Anbieter für SQLXML-Funktionen verwenden möchten, legen Sie die **SQLXML-Version** -Eigenschaft auf "SQLXML. 4.0" fest.  
  
  
