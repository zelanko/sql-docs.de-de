---
title: FOR XML-Sicherheitsüberlegungen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d7dd5294b96545c0b0f03d1e82bd1e7fd2799921
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52757152"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a>FOR XML-Sicherheitsüberlegungen (SQLXML 4.0)
  Der FOR XML AUTO-Modus erstellt eine XML-Hierarchie, in der Elementnamen Tabellennamen und Attributnamen Spaltennamen zugeordnet werden. Somit werden die Datenbanktabelle und die Spalteninformationen verfügbar gemacht. Sie können die Datenbankinformationen ausblenden, wenn Sie den AUTO-Modus (serverseitige Formatierung) verwenden, indem Sie Tabellen- und Spaltenaliasse in der Abfrage angeben. Diese Aliasse werden in dem resultierenden XML-Dokument als Element- und Attributsnamen zurückgegeben.  
  
 Die folgende Abfrage gibt beispielsweise den AUTO-Modus an, daher wird die XML-Formatierung auf dem Server durchgeführt:  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 Im resultierenden XML-Dokument werden die Aliasse für Element- und Attributsnamen verwendet:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 Wenn Sie den NESTED-Modus (clientseitige Formatierung) verwenden, werden Aliasse nur für Attribute im resultierenden XML-Dokument zurückgegeben. Die Namen der Basistabellen werden immer als Elementnamen zurückgegeben. Die folgende Abfrage gibt beispielsweise den NESTED-Modus an.  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 Im resultierenden XML-Dokument werden die Namen der Basistabellen als Elementnamen zurückgegeben; Tabellenaliasse werden nicht verwendet:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
