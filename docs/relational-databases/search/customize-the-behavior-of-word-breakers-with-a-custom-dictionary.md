---
title: Anpassen des Verhaltens der Wörtertrennung mit einem Benutzerwörterbuch | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.component: search
ms.reviewer: ''
ms.suite: sql
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 18a2aba8a554d0c08cf8a09ac0b5c5260d8855c7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Anpassen des Verhaltens der Wörtertrennung mit einem Benutzerwörterbuch
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können das Verhalten der Wörtertrennung für eine bestimmte Sprache anpassen, indem Sie eine sprachspezifische Benutzerwörterbuchdatei erstellen. Sie können z. B. verhindern, dass die Wörtertrennung bestimmte Begriffe oder Muster trennt.  
  
 Weitere Informationen finden Sie im folgenden SharePoint-Artikel:  
  
 [Erstellen eines Benutzerwörterbuchs (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 Speichern Sie Benutzerwörterbuchdateien für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in dem folgenden Ordner:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Starten Sie nach dem Erstellen oder Ändern von Benutzerwörterbuchdateien das Startprogramm für den SQL-Volltextfilterdaemon mit dem folgenden Befehl neu:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
