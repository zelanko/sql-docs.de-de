---
title: 'Schritt 1: Herstellen einer Verbindung mit der Datenquelle | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a104733c0e5ec5acc87eeabd00c4e51d4bfd000
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301350"
---
# <a name="step-1-connect-to-the-data-source"></a>Schritt 1: Herstellen der Verbindung mit der Datenquelle
Der erste Schritt in jeder Anwendung besteht darin, eine Verbindung mit der Datenquelle herzustellen. Diese Phase, einschließlich der darauf benötigenden Funktionen, wird in der folgenden Abbildung dargestellt.  
  
 ![Verbinden mit einer Datenquelle in einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Der erste Schritt beim Herstellen einer Verbindung mit der Datenquelle besteht darin, den Treiber-Manager zu laden und das Umgebungshandle mit **SQLAllocHandle**zuzuweisen. Weitere Informationen finden Sie unter [Zuweisen des Umgebungshandles](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Die Anwendung registriert dann die Version von ODBC, der sie entspricht, indem sie **SQLSetEnvAttr** mit dem SQL_ATTR_APP_ODBC_VER-Umgebungsattribut aufruft. Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) sowie der [Abwärtskompatibilität und Standardkonformität](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Als Nächstes weist die Anwendung ein Verbindungshandle mit **SQLAllocHandle** zu und stellt mit **SQLConnect**, **SQLDriverConnect**oder **SQLBrowseConnect**eine Verbindung mit der Datenquelle her. Weitere Informationen finden Sie unter [Zuweisen eines Verbindungshandles](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) und [Herstellen einer Verbindung](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Die Anwendung legt dann alle Verbindungsattribute fest, z. B. ob Transaktionen manuell festgeschrieben werden sollen. Weitere Informationen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).
