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
ms.openlocfilehash: 75082fed6b70c214b4f55b85034ffa371824d24f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85027125"
---
# <a name="how-extended-stored-procedures-work"></a>Funktionsweise erweiterter gespeicherter Prozeduren
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Der Funktionsablauf einer erweiterten gespeicherten Prozedur kann folgendermaßen beschrieben werden:  
  
1.  Wenn ein Client eine erweiterte gespeicherte Prozedur ausführt, wird die Anforderung in Tabular Data Stream (TDS) oder im SOAP-Format (Simple Object Access Protocol) von der Client Anwendung an übertragen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sucht nach der mit der erweiterten gespeicherten Prozedur verknüpften DLL und lädt diese DLL, falls dies nicht bereits geschehen ist.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruft die angeforderte erweiterte gespeicherte Prozedur, die als Funktion in der DLL implementiert ist, auf.  
  
4.  Die erweiterte gespeicherte Prozedur übergibt über die API für erweiterte gespeicherte Prozeduren Resultsets und Rückgabeparameter an den Server zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine – Programmierung der erweiterten gespeicherten Prozedur](../database-engine-extended-stored-procedure-programming.md)  
  
  
