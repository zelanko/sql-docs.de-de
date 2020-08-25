---
description: Überlegungen zur Sicherheit bei XML
title: Überlegungen zur XML-Sicherheit | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
author: rothja
ms.author: jroth
ms.openlocfilehash: f73261f51a457144010aec6871f2acbf083b0361
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88758970"
---
# <a name="xml-security-considerations"></a>Überlegungen zur Sicherheit bei XML
Die ADO-Speicher-und Open-Methoden des Recordset-Objekts werden nicht als sichere Vorgänge für die Ausführung in Internet Explorer angesehen. Wenn diese Methoden in einem Skriptcode verwendet werden, der in einer Anwendung oder einem Steuerelement ausgeführt wird, die in einem Browser gehostet wird, hat die Sicherheitskonfiguration des Browsers Auswirkungen auf das Verhalten.  
  
 Internet Explorer 5 bietet standardmäßig Sicherheitseinschränkungen für solche Vorgänge in den Internetzonen. Unter dieser Konfiguration kann das Recordset keinen Zugriff auf das lokale Dateisystem auf dem Client oder auf Datenquellen außerhalb der Domäne des Servers zugreifen, von dem die Seite heruntergeladen wurde. Insbesondere bei Ausführung innerhalb des Browser Hosts kann ein Recordset nur dann wieder in einer Datei gespeichert werden, wenn es sich auf dem Server befindet, von dem die Seite heruntergeladen wurde. Auf ähnliche Weise können Sie ein Recordset öffnen, indem Sie es nur aus einer Datei laden, wenn sich diese Datei auf demselben Server befindet, von dem die Seite heruntergeladen wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](./persisting-records-in-xml-format.md)