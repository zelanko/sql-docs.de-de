---
title: Anpassen des Verhaltens von Wörtertrennungen mithilfe eines benutzerdefinierten Wörterbuchs
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 806d2f7aa35fc3299f22dbd1c3423834aaa8936f
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056246"
---
# <a name="customize-behavior-of-word-breakers-with-a-custom-dictionary-sql-server-search"></a>Anpassen des Verhaltens von Wörtertrennungen mithilfe eines benutzerdefinierten Wörterbuchs (SQL Server-Suche)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Sie können das Verhalten der Wörtertrennung für eine bestimmte Sprache anpassen, indem Sie eine sprachspezifische Benutzerwörterbuchdatei erstellen. Sie können z. B. verhindern, dass die Wörtertrennung bestimmte Begriffe oder Muster trennt.  
  
 Weitere Informationen finden Sie im folgenden SharePoint-Artikel:  
  
 [Erstellen eines Benutzerwörterbuchs (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 Speichern Sie Benutzerwörterbuchdateien für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in dem folgenden Ordner:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Starten Sie nach dem Erstellen oder Ändern von Benutzerwörterbuchdateien das Startprogramm für den SQL-Volltextfilterdaemon mit dem folgenden Befehl neu:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
