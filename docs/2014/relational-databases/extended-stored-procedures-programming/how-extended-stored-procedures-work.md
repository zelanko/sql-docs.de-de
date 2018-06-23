---
title: Funktionsweise erweiterter gespeicherter Prozeduren | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8b51dc3d5e0401861e188814fd229753428ded9c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050537"
---
# <a name="how-extended-stored-procedures-work"></a>Funktionsweise erweiterter gespeicherter Prozeduren
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Der Funktionsablauf einer erweiterten gespeicherten Prozedur kann folgendermaßen beschrieben werden:  
  
1.  Wenn ein Client eine erweiterte gespeicherte Prozedur ausgeführt wird, wird die Anforderung im tabular Data Stream (TDS) oder (SOAP, Simple Object Access Protocol)-Format von der Clientanwendung zum Übertragen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sucht nach der mit der erweiterten gespeicherten Prozedur verknüpften DLL und lädt diese DLL, falls dies nicht bereits geschehen ist.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruft die angeforderte erweiterte gespeicherte Prozedur, die als Funktion in der DLL implementiert ist, auf.  
  
4.  Die erweiterte gespeicherte Prozedur übergibt über die API für erweiterte gespeicherte Prozeduren Resultsets und Rückgabeparameter an den Server zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine – Programmierung der erweiterten gespeicherten Prozedur](../database-engine-extended-stored-procedure-programming.md)  
  
  