---
description: Überlegungen zur Sicherheit bei XML
title: Überlegungen zur XML-Sicherheit | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
author: rothja
ms.author: jroth
ms.openlocfilehash: 608ad67d531573d0124ea312252e6d30c289bf15
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978791"
---
# <a name="xml-security-considerations"></a>Überlegungen zur Sicherheit bei XML
Die ADO-Speicher-und Open-Methoden des Recordset-Objekts werden nicht als sichere Vorgänge für die Ausführung in Internet Explorer angesehen. Wenn diese Methoden in einem Skriptcode verwendet werden, der in einer Anwendung oder einem Steuerelement ausgeführt wird, die in einem Browser gehostet wird, hat die Sicherheitskonfiguration des Browsers Auswirkungen auf das Verhalten.  
  
 Internet Explorer 5 bietet standardmäßig Sicherheitseinschränkungen für solche Vorgänge in den Internetzonen. Unter dieser Konfiguration kann das Recordset keinen Zugriff auf das lokale Dateisystem auf dem Client oder auf Datenquellen außerhalb der Domäne des Servers zugreifen, von dem die Seite heruntergeladen wurde. Insbesondere bei Ausführung innerhalb des Browser Hosts kann ein Recordset nur dann wieder in einer Datei gespeichert werden, wenn es sich auf dem Server befindet, von dem die Seite heruntergeladen wurde. Auf ähnliche Weise können Sie ein Recordset öffnen, indem Sie es nur aus einer Datei laden, wenn sich diese Datei auf demselben Server befindet, von dem die Seite heruntergeladen wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](./persisting-records-in-xml-format.md)