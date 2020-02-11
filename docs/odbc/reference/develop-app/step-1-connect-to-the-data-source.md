---
title: 'Schritt 1: Herstellen einer Verbindung mit der Datenquelle | Microsoft-Dokumentation'
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
ms.openlocfilehash: 80f2dfc05d9d27f60aca414ee0abd13e13b3ea65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114274"
---
# <a name="step-1-connect-to-the-data-source"></a>Schritt 1: Herstellen der Verbindung mit der Datenquelle
Der erste Schritt in einer Anwendung besteht darin, eine Verbindung mit der Datenquelle herzustellen. Diese Phase, einschließlich der erforderlichen Funktionen, ist in der folgenden Abbildung dargestellt.  
  
 ![Verbinden mit einer Datenquelle in einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Der erste Schritt beim Herstellen einer Verbindung mit der Datenquelle besteht darin, den Treiber-Manager zu laden und das Umgebungs Handle mit **SQLAllocHandle**zuzuordnen. Weitere Informationen finden Sie unter [Zuordnen des Umgebungs Handles](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Die Anwendung registriert dann die Version von ODBC, der Sie entspricht, indem Sie **SQLSetEnvAttr** mit dem SQL_ATTR_APP_ODBC_VER Environment-Attribut aufrufen. Weitere Informationen finden Sie unter [Deklarieren der ODBC-Version der Anwendung](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) und abwärts [Kompatibilität und Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Als nächstes ordnet die Anwendung ein Verbindungs Handle mit **sqlzugechandle** zu und stellt mit **SQLCONNECT**, **SQLDriverConnect**oder **sqlbrowseconnetct**eine Verbindung mit der Datenquelle her. Weitere Informationen finden Sie unter [Zuordnen eines Verbindungs Handles](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) und [Herstellen einer Verbindung](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Anschließend werden von der Anwendung alle Verbindungs Attribute festgelegt, z. b. ob Transaktionen manuell committen werden. Weitere Informationen finden Sie unter [Verbindungs Attribute](../../../odbc/reference/develop-app/connection-attributes.md).
