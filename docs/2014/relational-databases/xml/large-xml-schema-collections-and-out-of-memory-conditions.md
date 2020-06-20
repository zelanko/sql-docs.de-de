---
title: Große XML-Schemaauflistungen und Bedingungen des Typs „Nicht genügend Arbeitsspeicher“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443207bbbdff5db7e54d61fcebabe70e34cc540
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85013289"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Große XML-Schemaauflistungen und Bedingungen des Typs Nicht genügend Arbeitsspeicher
  Während eines Aufrufs der integrierten XML_SCHEMA_NAMESPACE()-Funktion für eine große XML-Schemaauflistung oder beim Löschen großer XML-Schemaauflistungen kann eine Bedingung des Typs "Nicht genügend Arbeitsspeicher" auftreten. Mit den folgenden Lösungen kann dieses Problem behoben werden:  
  
-   Wenn die Systemlast hoch ist, verwenden Sie den DROP_XML_SCHEMA_COLLECTION-Befehl. Schlägt dies fehl, schalten Sie die Datenbank mithilfe der ALTER DATABASE-Anweisung in den Einzelbenutzermodus um und versuchen dann nochmals, DROP XML SCHEMA COLLECTION auszuführen. Wenn die XML-Schemaauflistung in **master**-, **model**- oder **tempdb**-Datenbanken vorhanden ist, ist ein Neustart des Servers für den Einzelbenutzermodus erforderlich.  
  
-   Wenn Sie XML_SCHEMA_NAMESPACE aufrufen, können Sie versuchen, einen einzelnen XML-Schemanamespace abzurufen. Sie können den Aufruf auch zu einem Zeitpunkt durchführen, wenn die Systemlast geringer ist, oder den Aufruf im Einzelbenutzermodus versuchen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anforderungen und Einschränkungen für XML-Schemaauflistungen auf dem Server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
