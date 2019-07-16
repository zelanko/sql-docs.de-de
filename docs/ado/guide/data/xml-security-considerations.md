---
title: XML-Sicherheitsüberlegungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa0e9e2df1e8ba3f44b10e662d25e536ac7962f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923357"
---
# <a name="xml-security-considerations"></a>Überlegungen zur Sicherheit bei XML
Die ADO zu speichern und Öffnen von Methoden für das Recordset-Objekt gelten nicht sichere Vorgänge in Internet Explorer ausgeführt. Also, wenn diese Methoden in einem Serverskript-Code verwendet werden, die ausgeführt wird, in einer Anwendung oder ein Steuerelement, das in einem Browser gehostet wird, wird die Sicherheitskonfiguration des Browsers auf deren Verhalten auswirken.  
  
 Internet Explorer 5 stellt die sicherheitseinschränkungen für Vorgänge dieser Art standardmäßig in der Internetzone. Unter dieser Konfiguration kann nicht das Recordset stellen keinen Zugriff auf dem lokalen Dateisystem auf dem Client oder den Zugriff auf alle Datenquellen außerhalb der Domäne des Servers, von dem die Seite heruntergeladen wurde. Insbesondere kann bei der Ausführung im Browser-Host ein Recordset zurück in eine Datei gespeichert werden, wenn sie auf dem gleichen Server befindet, von dem die Seite heruntergeladen wurde. Auf ähnliche Weise können Sie ein Recordset öffnen, indem Sie sie aus einer Datei laden, nur dann, wenn die Datei auf dem gleichen Server wird von dem die Seite heruntergeladen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
