---
title: Funktionsweise erweiterter gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9b52e8fd5cda7d0b05ebbddbb422f74bd81b1993
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804112"
---
# <a name="how-extended-stored-procedures-work"></a>Funktionsweise erweiterter gespeicherter Prozeduren
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Der Funktionsablauf einer erweiterten gespeicherten Prozedur kann folgendermaßen beschrieben werden:  
  
1.  Wenn ein Client eine erweiterte gespeicherte Prozedur ausgeführt wird, wird die Anforderung in tabular Data Stream (TDS) oder (SOAP, Simple Object Access Protocol)-Format von der Clientanwendung zu übertragen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sucht nach der mit der erweiterten gespeicherten Prozedur verknüpften DLL und lädt diese DLL, falls dies nicht bereits geschehen ist.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruft die angeforderte erweiterte gespeicherte Prozedur, die als Funktion in der DLL implementiert ist, auf.  
  
4.  Die erweiterte gespeicherte Prozedur übergibt über die API für erweiterte gespeicherte Prozeduren Resultsets und Rückgabeparameter an den Server zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine – Programmierung der erweiterten gespeicherten Prozedur](../database-engine-extended-stored-procedure-programming.md)  
  
  
