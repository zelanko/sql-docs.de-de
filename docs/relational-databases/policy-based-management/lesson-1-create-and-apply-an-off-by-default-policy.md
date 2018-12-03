---
title: 'Lektion 1: Erstellen und Anwenden einer Richtlinie „Standardmäßig aus“ | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: security
ms.prod_service: database-engine
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d31367db-b7db-44c4-8df2-f1240474cf78
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 678f9da12655cc733dcdf95aca5f61e5aa1cd45e
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158622"
---
# <a name="lesson-1-create-and-apply-an-off-by-default-policy"></a>Lektion 1: Erstellen und Anwenden einer Richtlinie 'Standardmäßig aus'
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Mit richtlinienbasierten Verwaltungsrichtlinien können Sie ein oder mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein oder mehrere Instanzobjekte, Serverinstanzen, ein oder mehrere Datenbanken oder ein oder mehrere Datenbankobjekte verwalten. Als Datenbankadministrator möchten Sie sicherstellen, dass auf bestimmten Servern keine Datenbank-E-Mail aktiviert ist. In dieser Lektion erstellen Sie eine Bedingung und eine Richtlinie, durch die diese Serveroption festgelegt wird. Sie testen den Server, um zu sehen, ob er die Richtlinie einhält. Anschließend verwenden Sie die Richtlinie, um den Server neu zu konfigurieren, sodass der Server die Richtlinie einhält.  

## <a name="prerequisites"></a>Voraussetzungen
Zur Durchführung dieses Tutorials benötigen Sie SQL Server Management Studio und Zugriff auf einen Server, auf dem SQL Server ausgeführt wird. 

- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installieren Sie die [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
  
## <a name="create-the-mail-off-condition"></a>Erstellen der Bedingung „Mail aus“

1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, erweitern Sie **Richtlinienverwaltung**, erweitern Sie **Facets**, klicken Sie mit der rechten Maustaste auf **Oberflächenkonfiguration**und anschließend auf **Neue Bedingung**.  

    ![Neue Bedingung](Media/lesson-1-create-and-apply-an-off-by-default-policy/new-surface-area-condition.png)
  
2.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen **Mail aus**ein.   
    1. Bestätigen Sie im Feld **Facet** , dass das Facet **Oberflächenkonfiguration** ausgewählt ist.
    1. Geben Sie im Dialogfeld **Ausdruck** im Feld **Feld** den Ausdruck **@DatabaseMailEnabled**aus, wählen Sie im Feld **Operator** die Option **=** aus, und wählen Sie im Feld **Wert** die Option **False**.  
    1. Geben Sie auf der Seite **Beschreibung** eine Beschreibung der Bedingung ein, und klicken Sie dann auf **OK** , um die Bedingung zu erstellen.  

    ![Bedingung „Mail aus“](Media/lesson-1-create-and-apply-an-off-by-default-policy/mail-off-condition.png) 
  
## <a name="create-the-off-by-default-policy"></a>Erstellen der Richtlinie „Standardmäßig aus“  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Oberflächenkonfiguration**und anschließend auf **Neue Richtlinie**.  
  
2.  Geben Sie im Dialogfeld **Neue Richtlinie erstellen** im Feld **Name** den Namen **Standardmäßig aus**ein. 
    1. Lassen Sie das Kontrollkästchen **Aktiviert** deaktiviert. Das Kontrollkästchen **Aktiviert** gilt für automatisierte Richtlinien, und diese Richtlinie wird bei Bedarf ausgeführt.
    1. Führen Sie im Kontrollkästchen **Bedingung überprüfen** einen Bildlauf nach unten zum Bereich **Oberflächenkonfiguration** durch, und wählen Sie dann **Mail aus** als die zu überprüfende Bedingung aus.
    1. Das Feld **Für Ziele** ist leer, da dies eine serverbezogene Richtlinie ist. 
    1. Wählen Sie im Feld **Auswertungsmodus** den Modus **Bedarfsgesteuert** aus.
    1. Wählen Sie im Feld **Serverbeschränkung** die Option **Keine**aus.
    1. Geben Sie auf der Seite **Beschreibung** eine Beschreibung der Richtlinie ein.  

    ![Richtlinie „Standardmäßig aus“](Media/lesson-1-create-and-apply-an-off-by-default-policy/off-by-default-policy.png)
  
9. Auf der Beschreibungsseite können Sie im Bereich **Zusätzlicher Hilfelink** einen Link zu einer Webseite für Ihre Richtlinien bereitstellen. Geben Sie im Feld **Anzuzeigender Text** den Text ein, der für den Link angezeigt wird.
    1. Geben Sie in das Feld **Adresse** einen Link zu einer Hilfeseite ein, z. B. die Startseite der IT-Abteilung Ihres Unternehmens.
    1. Um diese Webseite zur Bestätigung der Adresse zu öffnen, klicken Sie auf **Link testen**.
    1. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

    ![Weblink für die Richtlinie „Standardmäßig aus“](Media/lesson-1-create-and-apply-an-off-by-default-policy/off-by-default-policy-web-link.png)


## <a name="configure-server-to-run-off-by-default-policy"></a>Konfigurieren eines Servers für das Ausführen der Richtlinie „Standardmäßig aus“ 

1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], zeigen Sie auf **Richtlinien**, und klicken Sie anschließend auf **Auswerten**.  

    ![Auswerten der Richtlinie](Media/lesson-1-create-and-apply-an-off-by-default-policy/evaluate-policy.png)
  
2.  Im Dialogfeld **Richtlinien auswerten** können Sie Richtlinien aus einer anderen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder aus einer Datei auswählen. Für diesen Schritt belassen Sie als Einstellung für **Quelle** Ihre Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
    1. Wählen Sie im Abschnitt **Richtlinien** die Richtlinie **Standardmäßig aus** aus.
    1. Um zu sehen, ob der Server diese Richtlinie einhält, klicken Sie auf **Auswerten**.
    1. Im Bereich **Ergebnisse** wird ein grüner Kreis mit einem Häkchen angezeigt, wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Richtlinie einhält. Ein roter Kreis mit einem X wird angezeigt, wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Richtlinie nicht einhält. 

   ![Auswerten der Richtlinie „Standardmäßig aus“](Media/lesson-1-create-and-apply-an-off-by-default-policy/evaluate-off-by-default-policy.png)

  
6.  Im Bereich **Zieldetails** werden weitere Informationen in der Spalte **Meldung** angezeigt, wenn ein Fehler auftritt. Klicken Sie in der Spalte **Meldung** auf **Anzeigen** , um einen Bericht anzuzeigen, der die Überprüfungsergebnisse für jede überprüfte Facet-Eigenschaft enthält. 

    ![Anzeigen der Ergebnisse einer Richtlinienauswertung ](Media/lesson-1-create-and-apply-an-off-by-default-policy/view-results-of-policy-evaluation.png)
  
7.  Die Richtlinienbeschreibung wird unten auf der Seite angezeigt, und im Abschnitt **Zusätzliche Hilfe** wird der Link angezeigt, den Sie für die Richtlinie konfiguriert haben. Klicken Sie auf den Meldungslink, um die Webseite zu öffnen, die Sie beim Erstellen der Richtlinie angegeben haben.   

1.  Schließen Sie den Browser, und schließen Sie dann das Dialogfeld **Ergebnisse, Detailansicht** .  

1. Wenn der Server die Richtlinie nicht einhält und Sie Datenbank-E-Mail deaktivieren möchten, klicken Sie auf der Seite **Auswertungsergebnisse** auf **Anwenden** .  
  
10. Schließen Sie das Dialogfeld **Ergebnisse, Detailansicht** und das Dialogfeld **Richtlinien auswerten** .   

   
## <a name="next-lesson"></a>Nächste Lektion  
[Lektion 2: Erstellen und Anwenden einer Richtlinie für Benennungsstandards](../../relational-databases/policy-based-management/lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
  
