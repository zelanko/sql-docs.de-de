---
title: Herstellen einer Verbindung mit SQLDriverConnect | Microsoft-Dokumentation
description: SQLDriverConnect bietet zusätzliche Verbindungsfunktionen über SQLConnect, einschließlich Optionen, um den Benutzer zur Eingabe weiterer Informationen aufzufordern.
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78186e903405aa1b59cfac185e62646dbda6e77a
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88746170"
---
# <a name="connecting-with-sqldriverconnect"></a>Herstellen einer Verbindung mit SQLDriverConnect

**SQLDriverConnect** wird zum Herstellen einer Verbindung mit einer Datenquelle mithilfe einer Verbindungs Zeichenfolge verwendet. **SQLDriverConnect** wird für die folgenden Szenarien anstelle von **SQLCONNECT** verwendet:  
  
- Stellen Sie eine Verbindung mithilfe einer Verbindungs Zeichenfolge her, die den Datenquellen Namen, eine oder mehrere Benutzer-IDs, ein oder mehrere Kenn Wörter und andere Informationen enthält, die von der Datenquelle benötigt werden.  
  
- Herstellen einer Verbindung mithilfe einer partiellen Verbindungs Zeichenfolge oder ohne zusätzliche Informationen in diesem Fall können der Treiber-Manager und der Treiber alle den Benutzer zur Eingabe von Verbindungsinformationen auffordern.  
  
- Stellen Sie eine Verbindung mit einer Datenquelle her, die nicht in den Systeminformationen definiert ist. Wenn die Anwendung eine partielle Verbindungs Zeichenfolge bereitstellt, kann der Treiber den Benutzer zur Eingabe von Verbindungsinformationen auffordern.  
  
- Stellen Sie eine Verbindung mit einer Datenquelle her, indem Sie eine aus den Informationen in einer DSN-Datei erstellte Verbindungs Zeichenfolge verwenden.  
  
Nachdem eine Verbindung hergestellt wurde, gibt **SQLDriverConnect** die abgeschlossene Verbindungs Zeichenfolge zurück. Die Anwendung kann diese Zeichenfolge für nachfolgende Verbindungsanforderungen verwenden.

In diesem Abschnitt werden die folgenden Themen behandelt:  
  
- [Treiberspezifische Verbindungsinformationen](driver-specific-connection-information.md)  
  
- [Aufforderung an Benutzer zur Eingabe von Verbindungsinformationen](prompting-the-user-for-connection-information.md)  
  
- [Herstellen einer Verbindung mithilfe von Dateidatenquellen](connecting-using-file-data-sources.md)  
  
- [Herstellen einer Verbindung direkt mit Treibern](connecting-directly-to-drivers.md)
