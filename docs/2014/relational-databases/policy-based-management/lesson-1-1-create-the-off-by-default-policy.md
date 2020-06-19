---
title: Erstellen der Richtlinie „Standardmäßig aus“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 98fde3c5-297c-4d95-981e-95700bbf5ccd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b85d267cd56fdf64b6235f551b84f32e4353b2d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063791"
---
# <a name="create-the-off-by-default-policy"></a>Erstellen der Richtlinie 'Standardmäßig aus'
  In dieser Aufgabe erstellen Sie eine Bedingung mit dem Namen Mail aus, die auf dem Oberflächenkonfigurationsfacet basiert. Anschließend erstellen Sie eine Richtlinie mit dem Namen Standardmäßig aus.  
  
### <a name="to-create-the-mail-off-condition"></a>So erstellen Sie die Bedingung 'Mail aus'  
  
1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, erweitern Sie **Richtlinienverwaltung**, erweitern Sie **Facets**, klicken Sie mit der rechten Maustaste auf **Oberflächenkonfiguration**und anschließend auf **Neue Bedingung**.  
  
2.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen **Mail aus**ein.  
  
3.  Bestätigen Sie im Feld **Facet** , dass das Facet **Oberflächenkonfiguration** ausgewählt ist.  
  
4.  Wählen Sie im Bereich **Ausdruck** im **Feld Feld** die ** \@ Option databasemailaktivierte**aus, wählen Sie im Feld **Operator** die Option aus **=** , und wählen Sie im Feld **Wert** **false**aus.  
  
5.  Geben Sie auf der Seite **Beschreibung** eine Beschreibung der Bedingung ein, und klicken Sie dann auf **OK** , um die Bedingung zu erstellen.  
  
### <a name="to-create-the-off-by-default-policy"></a>So erstellen Sie die Richtlinie 'Standardmäßig aus'  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Oberflächenkonfiguration**und anschließend auf **Neue Richtlinie**.  
  
2.  Geben Sie im Dialogfeld **Neue Richtlinie erstellen** im Feld **Name** den Namen **Standardmäßig aus**ein.  
  
3.  Lassen Sie das Kontrollkästchen **Aktiviert** deaktiviert. Das Kontrollkästchen **Aktiviert** gilt für automatisierte Richtlinien, und diese Richtlinie wird bei Bedarf ausgeführt.  
  
4.  Führen Sie im Kontrollkästchen **Bedingung überprüfen** einen Bildlauf nach unten zum Bereich **Oberflächenkonfiguration** durch, und wählen Sie dann **Mail aus** als die zu überprüfende Bedingung aus.  
  
5.  Das Feld **Für Ziele** ist leer, da dies eine serverbezogene Richtlinie ist.  
  
6.  Wählen Sie im Feld **Auswertungsmodus** den Modus **Bedarfsgesteuert** aus.  
  
7.  Wählen Sie im Feld **Serverbeschränkung** die Option **Keine**aus.  
  
8.  Geben Sie auf der Seite **Beschreibung** eine Beschreibung der Richtlinie ein.  
  
9. Sie können im Bereich **Zusätzlicher Hilfelink** einen Link zu einer Webseite für Ihre Richtlinien bereitstellen. Geben Sie im Feld **Anzuzeigender Text** den Text ein, der für den Link angezeigt wird.  
  
10. Geben Sie in das Feld **Adresse** einen Link zu einer Hilfeseite ein, z. B. die Startseite der IT-Abteilung Ihres Unternehmens.  
  
11. Um diese Webseite zur Bestätigung der Adresse zu öffnen, klicken Sie auf **Link testen**.  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Konfigurieren eines Servers für das Ausführen der Richtlinie 'Standardmäßig aus'](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
  
