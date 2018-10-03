---
title: Das &lt;xsd:redefine&gt;-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dfed461589882e91f4fa4ec2394bc858def67d96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48182270"
---
# <a name="the-ltxsdredefinegt-element"></a>Das &lt;xsd:redefine&gt;-Element
  Das W3C XSD **redefine** -Element stellt Unterstützung zum Neudefinieren von Schemakomponenten zur Verfügung. Unterstützung für diese Richtlinie ist die Leistung beeinträchtigen und außerdem, dass erfordert jedoch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erneut überprüfen alle Instanzen der `xml` mit dem neu definierten Schema verknüpft sind. Deshalb unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dieses Element nicht. XML-Schemas, die das **\<xsd:redefine>**-Element enthalten, werden vom Server zurückgewiesen.  
  
 Gehen Sie zum Aktualisieren des Schemas oder seiner Komponenten stattdessen folgendermaßen vor:  
  
1.  Erstellen Sie eine neue XML-Schemaauflistung mit den geänderten Schemakomponenten.  
  
2.  Ändern Sie alle `xml`-Datentypen (XML DT), welche die neu zu definierende XML-Schemaauflistung verwenden so ab, dass sie stattdessen die neue XML-Schemaauflistung verwenden. Hierzu verwenden Sie die ALTER COLUMN-Option des ALTER TABLE-Befehls, um den Spaltentyp zu ändern, oder Sie ändern die für Variablen oder Parameter geltenden Einschränkungen der XML-Schemaauflistung.  
  
3.  Löschen Sie die alte Version der XML-Schemaauflistung.  
  
## <a name="see-also"></a>Siehe auch  
 [Anforderungen und Einschränkungen für XML-Schemaauflistungen auf dem Server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
