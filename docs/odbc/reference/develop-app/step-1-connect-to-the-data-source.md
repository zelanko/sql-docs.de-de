---
title: 'Schritt 1: Verbinden mit der Datenquelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 154fdd7368835ba2a578d3ec641705c4064859ac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600898"
---
# <a name="step-1-connect-to-the-data-source"></a>Schritt 1: Herstellen der Verbindung mit der Datenquelle
Der erste Schritt bei jeder Anwendung ist für die Verbindung mit der Datenquelle. In dieser Phase, einschließlich der Funktionen, die es erforderlich ist, die wird in der folgenden Abbildung angezeigt.  
  
 ![Herstellen einer Verbindung mit der Datenquelle in einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Der erste Schritt beim Herstellen einer Verbindung mit der Datenquelle wird zum Laden der Treiber-Manager und Zuordnen des Umgebungshandles mit **SQLAllocHandle**. Weitere Informationen finden Sie unter [zuordnen, die Umgebung behandeln](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Klicken Sie dann die Anwendung registriert, der sie durch den Aufruf entspricht, ODBC-Version **SQLSetEnvAttr** mit dem SQL_ATTR_APP_ODBC_VER Umgebung-Attribut. Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) und [Abwärtskompatibilität und zur Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Als Nächstes ordnet die Anwendung ein Verbindungshandle mit **SQLAllocHandle** und eine Verbindung mit der Datenquelle mit **SQLConnect**, **SQLDriverConnect**, oder **SQLBrowseConnect**. Weitere Informationen finden Sie unter [zuordnen, eine Verbindung behandeln](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) und [Herstellen einer Verbindung](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Klicken Sie dann die Anwendung legt die Verbindungsattribute, z. B. ob manuellen commit der Transaktionen fest. Weitere Informationen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).
