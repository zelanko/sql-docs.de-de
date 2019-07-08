---
title: Filter generieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14ccac181a4b76f8fc0423d6e00b20f91f8ea9cc
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67581359"
---
# <a name="generate-filters"></a>Filter generieren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mithilfe des Dialogfelds **Filter generieren** können Sie einen Zeilenfilter für eine Tabelle in einer Mergeveröffentlichung definieren. Die Replikation erweitert dann den Filter automatisch auf andere Tabellen, die durch Fremdschlüsselbeziehungen verbunden sind. Wenn Sie z. B. einen Filter für eine Kundentabelle so definieren, dass diese nur Daten zu französischen Kunden enthält, dann erweitert die Replikation den Filter derart, dass verknüpfte Tabellen mit Bestellungen und Bestellungsdetails nur Informationen enthalten, die sich auf französische Kunden beziehen.  
  
## <a name="options"></a>enthalten  
 Dieses Dialogfeld enthält einen dreistufigen Vorgang zum Erstellen eines Zeilenfilters für eine Tabelle. Der Filter wird dann auf die Tabellen erweitert, die mit der gefilterten Tabelle über Primärschlüssel- und Fremdschlüsselbeziehungen verknüpft sind. Wenn z. B. drei Tabellen gegeben sind, **Customer**, **SalesOrderHeader**und **SalesOrderDetail**, mit einer Beziehung zwischen **Customer** und **SalesOrderHeader**sowie einer Beziehung zwischen **SalesOrderHeader** und **SalesOrderDetail**, dann können Sie einen Zeilenfilter auf **Customer**anwenden, und die Replikation erweitert diesen Filter auf **SalesOrderHeader** und **SalesOrderDetail**.  
  
1.  **Wählen Sie die zu filternde Tabelle aus.**  
  
     Wählen Sie eine Tabelle aus dem Dropdownlistenfeld aus. Tabellen werden im Listenfeld nur dann angezeigt, wenn sie auf der Seite **Artikel** ausgewählt wurden.  
  
2.  **Vervollständigen Sie die Filteranweisung, um die von Abonnenten empfangenen Tabellenzeilen zu identifizieren.**  
  
     Definieren Sie eine neue Filteranweisung. Im Listenfeld **Spalten** werden alle Spalten aufgeführt, die Sie aus einer in **Wählen Sie die zu filternde Tabelle aus**ausgewählten Tabelle veröffentlichen. Der Textbereich **Filteranweisung** enthält den Standardtext im folgenden Format:  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     Der Text kann nicht geändert werden. Geben Sie die Filterklausel nach dem WHERE-Schlüsselwort mithilfe der standardmäßigen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax ein.  
  
    > [!IMPORTANT]  
    >  Aus Leistungsgründen ist es empfehlenswert, keine Funktionen auf Spaltennamen in Klauseln für parametrisierte Zeilenfilter anzuwenden, wie z. B. `LEFT([MyColumn]) = SUSER_SNAME()`. Wenn Sie HOST_NAME in einer Filterklausel verwenden und den HOST_NAME-Wert überschreiben, müssen Datentypen eventuell mit CONVERT konvertiert werden. Weitere Informationen zu bewährten Methoden für diesen Fall finden Sie im Abschnitt über das Überschreiben des HOST_NAME()-Werts im Thema [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
3.  **Geben Sie an, wie viele Abonnements Daten aus dieser Tabelle empfangen.**  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only. Merge replication allows you to specify the type of partitions that are best suited to your data and application. If you select **A row from this table will go to only one subscription**, merge replication sets the nonoverlapping partitions option. Nonoverlapping partitions work in conjunction with precomputed partitions to improve performance, with nonoverlapping partitions minimizing the upload cost associated with precomputed partitions. The performance benefit of nonoverlapping partitions is more noticeable when the parameterized filters and join filters used are more complex. If you select this option, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber. For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
 Nachdem Sie einen Filter hinzugefügt haben, klicken Sie auf **OK** , um das Dialogfeld zu schließen. Der von Ihnen angegebene Filter wird analysiert und für die Tabelle in der SELECT-Klausel ausgeführt. Wenn die Filteranweisung Syntaxfehler oder andere Probleme enthält, werden Sie benachrichtigt und können die Filteranweisung bearbeiten.  
  
 Nachdem die Anweisung analysiert ist, erstellt die Replikation die erforderlichen Joinfilter. Wenn Sie bis jetzt für den Verleger, für den der Assistent ausgeführt wird, den Verteiler nicht konfiguriert haben, werden Sie jetzt aufgefordert, ihn zu konfigurieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtern von veröffentlichten Daten](../../relational-databases/replication/publish/filter-published-data.md)   
 [Join Filters](../../relational-databases/replication/merge/join-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
