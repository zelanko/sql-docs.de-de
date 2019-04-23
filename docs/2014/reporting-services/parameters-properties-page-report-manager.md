---
title: Parameter (Eigenschaftenseite) (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: ebb53598-2378-46ae-8935-d5192f8ea49a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f83e66d238aa67b28bf547540c5a6b5dfcc9c92d
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59969046"
---
# <a name="parameters-properties-page-report-manager"></a>Parameter (Eigenschaftenseite) (Berichts-Manager)
  Verwenden Sie die Eigenschaftenseite Parameter, um Parametereinstellungen für einen parametrisierten Bericht anzuzeigen oder zu ändern.  
  
 Parameter werden in der Berichtsdefinition angegeben, bevor der Bericht veröffentlicht wird. Nach der Veröffentlichung eines Berichts können einige Parametereigenschaftswerte geändert werden. Welche Werte geändert werden können, hängt von der Definition der Parameter im Bericht ab. Wenn beispielsweise eine Liste statischer Werte für einen Parameter definiert ist, können Sie einen anderen statischen Wert als Standardwert auswählen. Es können jedoch keine Werte hinzugefügt oder aus der Liste entfernt werden. Falls der Parameter auf einer Abfrage basiert, werden ebenso alle Aspekte dieser Abfrage (einschließlich des verwendeten Datasets, ob NULL-Werte oder leere Werte zugelassen sind und ob ein Standardwert bereitgestellt wird) im Bericht vor seiner Veröffentlichung definiert.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-parameters-properties-page"></a>So öffnen Sie die Eigenschaftenseite "Parameter"  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie Parametereinstellungen ändern möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet.  
  
4.  Wählen Sie die Registerkarte **Parameter** aus. Wenn die Registerkarte **Parameter** nicht angezeigt wird, enthält der Bericht keine Parameter.  
  
## <a name="options"></a>Optionen  
 **Parametername**  
 Gibt den Namen des Parameters an.  
  
 **Datentyp**  
 Gibt den Datentyp des Parameters an.  
  
 **Hat Standardwert**  
 Aktivieren Sie dieses Kontrollkästchen, um anzugeben, ob der Parameter über einen Standardwert verfügt. Durch das Aktivieren dieses Kontrollkästchens wird die Option **Standardwert**aktiviert. Wenn der Berichtsparameter NULL-Werte akzeptiert, wird auch die Option **NULL** aktiviert. Ist **Besitzt Standardwert** nicht aktiviert, müssen Sie entweder den Wert ausblenden oder während der Ausführung des Berichts den Benutzer auffordern, einen Wert anzugeben.  
  
 **Standardwert**  
 Geben Sie einen Wert für den Parameter an. Um einen Standardwert anzugeben, muss die Option **Besitzt Standardwert** aktiviert sein, während **NULL** nicht aktiviert sein darf. Ein Standardwert kann durch die Berichtsdefinition bereitgestellt werden. Falls **Standardwert** mit einem oder mehreren statischen Werten aufgefüllt ist, werden diese Werte mit dem Bericht erstellt. Falls **Standardwert** den Wert **Abfragebasiert**hat, wird der Parameterwert durch eine Abfrage ermittelt, die im Bericht definiert ist.  
  
 Falls **Standardwert** einen Wert akzeptiert, können Sie eine Konstante oder Syntax eingeben, die für die mit dem Bericht verwendete Datenverarbeitungserweiterung gültig ist. Wenn die Abfragesprache der Datenverarbeitungserweiterung beispielsweise Platzhalterzeichen unterstützt, können Sie ein Platzhalterzeichen als Standardwert angeben.  
  
 Wenn Sie anschließend angeben, dass dem Benutzer eine Eingabeaufforderung angezeigt wird, wird der Standardwert als Anfangswert verwendet, den Benutzer verwenden oder auch ändern können. Wenn keine Eingabeaufforderung für den Parameterwert angezeigt wird, wird dieser Wert für alle Benutzer verwendet, die den Bericht ausführen.  
  
 **NULL**  
 Aktivieren Sie dieses Kontrollkästchen, um NULL als Standardwert anzugeben. Ein NULL-Wert bedeutet, dass der Bericht ausgeführt werden kann, auch wenn der Benutzer keinen Parameterwert bereitstellt. Falls in dieser Spalte kein Kontrollkästchen angezeigt wird, akzeptiert der Parameter keine NULL-Werte.  
  
 **Hide**  
 Aktivieren Sie dieses Kontrollkästchen, um den Parameter im Parameterbereich auszublenden, der oben im Bericht angezeigt wird. Der Parameter wird weiterhin in den Abonnementsdefinitionsseiten angezeigt und kann ebenso noch in einer Berichts-URL angegeben werden. Das Ausblenden des Parameters ist hilfreich, wenn Sie den Bericht immer mit dem von Ihnen angegebenen Standardwert ausführen möchten.  
  
 Deaktivieren Sie dieses Kontrollkästchen, wenn Sie möchten, dass der Parameter im Bericht sichtbar ist.  
  
 **Eingabeaufforderung für Benutzer**  
 Aktivieren Sie dieses Kontrollkästchen, um ein Textfeld mit einer Eingabeaufforderung für einen Parameterwert anzuzeigen.  
  
 Deaktivieren Sie dieses Kontrollkästchen, wenn Sie den Bericht im unbeaufsichtigten Modus ausführen möchten (z. B., um Momentaufnahmen vom Berichtsverlauf oder der Berichtsausführung zu generieren), wenn Sie denselben Parameterwert für alle Benutzer verwenden möchten oder wenn keine Benutzereingabe für den Wert erforderlich ist.  
  
 **Anzeigetext**  
 Stellen Sie eine Textzeichenfolge bereit, die neben dem Parametertextfeld angezeigt wird. Diese Zeichenfolge enthält eine Bezeichnung oder beschreibenden Text. Die Länge der Zeichenfolge ist nicht begrenzt. Längere Textzeichenfolgen werden innerhalb des vorhandenen Platzes umbrochen.  
  
## <a name="see-also"></a>Siehe auch  
 [Allgemeine Eigenschaften (Seite) (Berichte, Berichts-Manager)](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
