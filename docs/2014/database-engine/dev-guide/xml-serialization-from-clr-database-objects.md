---
title: XML-Serialisierung von CLR-Datenbankobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 646d15dc3091323e6e7db2af757640122fb2f0fd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62779778"
---
# <a name="xml-serialization-from-clr-database-objects"></a>XML-Serialisierung auf Grundlage von CLR-Datenbankobjekten
  Die XML-Serialisierung ist in zwei Szenarien erforderlich:  
  
-   Aufrufen von Webdiensten aus CLR-Objekten (Common Language Runtime)  
  
-   Konvertieren eines benutzerdefinierten Typs (UDT) in XML  
  
 Wenn durch Aufrufen der `XmlSerializer`-Klasse eine XML-Serialisierung durchgeführt wird, wird in der Regel eine zusätzliche Serialisierungsassembly erstellt, die in das Projekt mit der Quellassembly überladen wird. Aus Sicherheitsgründen wird diese Überladung jedoch in der CLR deaktiviert. Um daher einen Webdienst aufzurufen oder eine Konvertierung von UDT in XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auszuführen, muss die Assembly manuell mithilfe eines Tools namens **Sgen. exe** erstellt werden, das mit der .NET Framework bereitgestellt wird, die die erforderlichen Serialisierungsassemblys generiert. Beim Aufrufen von `XmlSerializer` muss die Serialisierungsassembly wie folgt manuell erstellt werden:  
  
1.  Führen Sie das Tool **Sgen. exe** aus, das mit dem .NET Framework SDK bereitgestellt wird, um die Assembly zu erstellen, die die XML-Serialisierer für die Quellassembly enthält.  
  
2.  Registrieren Sie die generierte Assembly mithilfe der `CREATE ASSEMBLY`-Anweisung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Informationen zu Fehlern, die beim Ausführen der XML-Serialisierung auftreten können, finden Sie im folgenden Microsoft-Support Artikel: ["kann dynamisch generierte Serialisierungsassembly nicht laden"](https://support.microsoft.com/kb/913668).  
  
 Informationen über Datentypen, die vom XML-Serialisierungsprogramm nicht unterstützt werden, finden Sie in der Dokumentation zu .NET Framework unter "Bindungsunterstützung für XML-Schema in .NET Framework".  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenzugriff von CLR-Datenbankobjekten](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
