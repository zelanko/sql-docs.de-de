---
description: Anpassen des Verhaltens von Wörtertrennungen mithilfe eines benutzerdefinierten Wörterbuchs (SQL Server-Suche)
title: Anpassen des Verhaltens von Wörtertrennungen mithilfe eines benutzerdefinierten Wörterbuchs
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.custom: seo-lt-2019
ms.openlocfilehash: 029e0914f7b9e8b62799ab4e5eaff57cdbca5aca
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460083"
---
# <a name="customize-behavior-of-word-breakers-with-a-custom-dictionary-sql-server-search"></a>Anpassen des Verhaltens von Wörtertrennungen mithilfe eines benutzerdefinierten Wörterbuchs (SQL Server-Suche)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Sie können das Verhalten der Wörtertrennung für eine bestimmte Sprache anpassen, indem Sie eine sprachspezifische Benutzerwörterbuchdatei erstellen. Sie können z. B. verhindern, dass die Wörtertrennung bestimmte Begriffe oder Muster trennt.  
  
 Weitere Informationen finden Sie im folgenden SharePoint-Artikel:  
  
 [Erstellen eines Benutzerwörterbuchs (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc263242(v=office.14))  
  
 Speichern Sie Benutzerwörterbuchdateien für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in dem folgenden Ordner:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Starten Sie nach dem Erstellen oder Ändern von Benutzerwörterbuchdateien das Startprogramm für den SQL-Volltextfilterdaemon mit dem folgenden Befehl neu:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
