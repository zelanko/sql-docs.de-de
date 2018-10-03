---
title: Anpassen des Verhaltens der Wörtertrennung mit einem Benutzerwörterbuch | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 50722b2773593662bb967fddc14ad1bc77c865f2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198330"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Anpassen des Verhaltens der Wörtertrennung mit einem Benutzerwörterbuch
  Sie können das Verhalten der Wörtertrennung für eine bestimmte Sprache anpassen, indem Sie eine sprachspezifische Benutzerwörterbuchdatei erstellen. Sie können z. B. verhindern, dass die Wörtertrennung bestimmte Begriffe oder Muster trennt.  
  
 Weitere Informationen finden Sie im folgenden SharePoint-Artikel:  
  
 [Erstellen eines Benutzerwörterbuchs (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 Speichern Sie Benutzerwörterbuchdateien für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in dem folgenden Ordner:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Starten Sie nach dem Erstellen oder Ändern von Benutzerwörterbuchdateien das Startprogramm für den SQL-Volltextfilterdaemon mit dem folgenden Befehl neu:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
