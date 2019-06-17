---
title: Datenquellen-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], file
- file data sources [ODBC]
ms.assetid: db245c80-981a-4638-bd03-69d04bc67af0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 733b958ee883aa62034b4acc1eec67100b35a74d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62628453"
---
# <a name="file-data-sources"></a>Dateidatenquellen
*Datei-Datenquellen* werden in einer Datei gespeichert und können Sie die Verbindungsinformationen, die wiederholt verwendet werden, indem Sie einen einzelnen Benutzer oder von mehreren Benutzern gemeinsam verwendet werden soll. Wenn eine Datei als Datenquelle verwendet wird, stellt der Treiber-Manager die Verbindung mit der Datenquelle anhand der Informationen in einer DSN-Datei her. Diese Datei kann wie jede andere Datei bearbeitet werden. Eine Datenquelle einen Datenquellennamen ein, keinen ist eine Datenquelle für den Computer, und nicht auf einen Benutzer oder Computer registriert ist.  
  
 Eine Dateidatenquelle optimiert die Verbindung hergestellt wird, da die DSN-Datei die Verbindungszeichenfolge enthält, die ansonsten für einen Aufruf von erstellt werden müssen die **SQLDriverConnect** Funktion. Ein weiterer Vorteil der DSN-Datei ist, dass es auf jedem Computer kopiert werden kann, damit identische Datenquellen an, die von vielen Computern verwendet werden können, solange sie den entsprechenden Treiber installiert haben. Eine Datenquelle kann auch von Anwendungen freigegeben werden. Eine freigegebenen Datenquelle kann in einem Netzwerk platziert werden und gleichzeitig von mehreren Anwendungen verwendet werden.  
  
 Eine DSN-Datei kann auch Dateidatenquelle sein. Eine Dateidatenquelle DSN-Datei befindet sich auf einem einzelnen Computer und verweist auf eine Datenquelle für den Computer. Dateidatenquelle vorhanden sein, vor allem um die einfache Konvertierung Quellen von maschinendaten in Dateidatenquellen zulassen, damit eine Anwendung entworfen werden kann, funktioniert nur mit Datei-Datenquellen. Wenn der Treiber-Manager die Informationen in eine Dateidatenquelle gesendet wird, verbindet ihn nach Bedarf für die Datenquelle für Computer, der auf die DSN-Datei verweist.  
  
 Weitere Informationen zu Datei-Datenquellen, finden Sie unter [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../odbc/reference/develop-app/connecting-using-file-data-sources.md), oder die [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) funktionsbeschreibung.
