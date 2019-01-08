---
title: Veröffentlichungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cb31bae59d95b01279a9fa84e02cd22c8017ca14
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52789382"
---
# <a name="publication-database"></a>Veröffentlichungsdatenbank
  Bei der Veröffentlichungsdatenbank handelt es sich um die Datenbank auf dem Verleger, die als Quelle der zu replizierenden Daten und Datenbankobjekte fungiert. Die in einer Replikation verwendeten Veröffentlichungsdatenbanken müssen aktiviert werden. Die Datenbank wird aktiviert, wenn ein Mitglied der festen Serverrolle **sysadmin** Folgendes ausführt:  
  
-   Erstellt eine Veröffentlichung auf der betreffenden Datenbank mithilfe des Assistenten für neue Veröffentlichung.  
  
-   Wählt die Datenbank im Dialogfeld **Verlegereigenschaften** aus.  
  
-   Führt **sp_replicationdboption** aus und legt für die Option **publish** (bei Momentaufnahme- oder Transaktionsveröffentlichungen) oder die Option **merge publish** (bei Mergeveröffentlichungen) **True**fest.  
  
## <a name="options"></a>Optionen  
 **Datenbanken**  
 Wählen Sie den Namen der Datenbank aus, die die Daten und Datenbankobjekte enthält, die veröffentlicht werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
