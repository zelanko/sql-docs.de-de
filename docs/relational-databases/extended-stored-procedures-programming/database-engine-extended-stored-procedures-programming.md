---
title: Programmierung von erweiterten gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- gateway applications [SQL Server]
- extended stored procedures [SQL Server], about extended stored procedures
- Open Data Services [SQL Server]
- ODS [SQL Server]
ms.assetid: 561305cd-c803-48af-9eec-2c19f4d311ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 541f24693598d20925dd37d4970c6d9916945793
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032012"
---
# <a name="database-engine-extended-stored-procedures---programming"></a>Datenbank-Engine: Programmierung der erweiterten gespeicherten Prozeduren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 In der Vergangenheit wurde Open Data Services verwendet, um Serveranwendungen zu schreiben, z. B. Gateways zu anderen Datenbankumgebungen als SQL Server. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die veralteten Teile der Open Data Services-API werden von nicht unterstützt. Der einzige weiterhin von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützte Bereich der ursprünglichen Open Data Services-API betrifft die Funktionen für erweiterte gespeicherte Prozeduren. Daher wurde die API umbenannt in "API für erweiterte gespeicherte Prozeduren".  
  
 Mit dem Erscheinen neuerer und leistungsfähigerer Technologien wie beispielsweise der verteilten Abfragen oder der CLR-Integration ist der Bedarf an Anwendungen, die auf die API für erweiterte gespeicherte Prozeduren zurückgreifen, weitgehend verschwunden.  
  
> [!NOTE]  
>  Für bereits bestehende Gateway-Anwendungen können Sie die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthaltene Datei opends60.dll nicht verwenden, um die Anwendungen auszuführen. Gateway-Anwendungen werden nicht mehr unterstützt.  
  
## <a name="extended-stored-procedures-vs-clr-integration"></a>Erweiterte gespeicherte Prozeduren im Vergleich zur CLR-Integration  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] boten erweiterte gespeicherte Prozeduren (XPs) den einzigen für Datenbankentwickler verfügbaren Mechanismus zum Erstellen serverseitiger Logik, die in [!INCLUDE[tsql](../../includes/tsql-md.md)] entweder schwierig auszudrücken oder unmöglich zu schreiben war. Die CLR-Integration bietet eine robustere Alternative zum Schreiben von solchen gespeicherten Prozeduren. Des Weiteren kann mit der CLR-Integration die Logik, die zuvor in der Form von gespeicherten Prozeduren geschrieben wurde, oft besser in Tabellenwertfunktionen ausgedrückt werden. So können die von der Funktion konstruierten Ergebnisse in SELECT-Anweisungen abgefragt werden, indem sie in die FROM-Klausel eingebettet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über die CLR-&#41; Integration in Common Language Runtime &#40;](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)   
 [CLR-Tabellenwertfunktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
  
  
