---
title: XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ad6b9ebaba9f05b0a927cd65f788cdbdb672a6d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163190"
---
# <a name="xml-serialization-from-clr-database-objects"></a>XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten
  Die XML-Serialisierung ist in zwei Szenarien erforderlich:  
  
-   Aufrufen von Webdiensten aus CLR-Objekten (Common Language Runtime)  
  
-   Konvertieren eines benutzerdefinierten Typs (UDT) in XML  
  
 Wenn durch Aufrufen der `XmlSerializer`-Klasse eine XML-Serialisierung durchgeführt wird, wird in der Regel eine zusätzliche Serialisierungsassembly erstellt, die in das Projekt mit der Quellassembly überladen wird. Aus Sicherheitsgründen wird diese Überladung jedoch in der CLR deaktiviert. Aus diesem Grund zum Aufrufen eines Webdiensts oder zum Ausführen der Konvertierung von UDT in XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Assembly muss erstellt werden, manuell mithilfe eines Tools namens **Sgen.exe** bereitgestellten mit .NET Framework, die die erforderlichen generiert. Serialisierungsassemblys. Beim Aufrufen von `XmlSerializer` muss die Serialisierungsassembly wie folgt manuell erstellt werden:  
  
1.  Führen Sie die **Sgen.exe** Tool, das das .NET Framework SDK zum Erstellen der Assembly mit den XML-Serialisierungsprogrammen für die Assembly der Ereignisquelle zur Verfügung steht.  
  
2.  Registrieren Sie die generierte Assembly mithilfe der `CREATE ASSEMBLY`-Anweisung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Informationen zu Fehlern, die beim Empfangen Sie möglicherweise Durchführen einer XML-Serialisierung finden Sie unter den folgenden Microsoft Support-Artikel: ["Dynamisch generiertes Serialisierungsassembly kann nicht geladen werden"](http://support.microsoft.com/kb/913668).  
  
 Informationen über Datentypen, die vom XML-Serialisierungsprogramm nicht unterstützt werden, finden Sie in der Dokumentation zu .NET Framework unter "Bindungsunterstützung für XML-Schema in .NET Framework".  
  
## <a name="see-also"></a>Siehe auch  
 [Datenzugriff von CLR-Datenbankobjekten aus](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
