---
title: Multithreadanwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 551a810d12d698124e1e9d0f78fcb0b37a113d6d
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707109"
---
# <a name="multithreaded-applications"></a>Multithreadanwendungen
  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ist ein Multithreadtreiber. Das Schreiben einer Multithreadanwendung ist eine Alternative zum Verwenden von asynchronen Aufrufen zur Verarbeitung von mehreren ODBC-Aufrufen. Ein Thread kann einen synchronen ODBC-Aufruf erstellen, und andere Threads können verarbeitet werden, während der erste Thread blockiert wird und auf die Antwort auf seinen Aufruf wartet. Dieses Modell ist effizienter als asynchrone Aufrufe, da Verarbeitungsaufwand beseitigt wird, wie Netzwerkverkehr und die wiederholte Erstellung von ODBC-Funktionsaufrufen zum Überprüfen von SQL_STILL_EXECUTING.  
  
 Der asynchrone Modus ist immer noch eine effektive Methode der Verarbeitung. Die Leistungsverbesserungen eines Multithreadmodells genügen nicht, um das Umschreiben asynchroner Anwendungen zu rechtfertigen. Wenn Benutzer DB-Library-Anwendungen konvertieren, die das asynchrone DB-Library-Modell verwenden, empfiehlt sich die Konvertierung in das asynchrone ODBC-Modell.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung](creating-a-driver-application.md)  
  
  
