---
title: Transformations-Editor für die DQS-Bereinigung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssdqs.designer.cleansing.f1
- SQL12.SSDQS.DESIGNER.DQCONNECTION.F1
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: cbb5ca8c048b42313b4776b4a2e4b99e44eec406
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66059416"
---
# <a name="dqs-cleansing-transformation-editor-dialog-box"></a>Transformations-Editor für die DQS-Bereinigung (Dialogfeld)
  Im Dialogfeld **Transformations-Editor für die DQS-Bereinigung** können Sie Daten mithilfe von Data Quality Services (DQS) korrigieren. Weitere Informationen finden Sie unter [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md).  
  
 Weitere Informationen zur Transformation finden Sie unter [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md).  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Transformations-Editors für die DQS-Bereinigung](#open)  
  
-   [Festlegen der Optionen auf der Registerkarte "Verbindungs-Manager"](#connection)  
  
-   [Festlegen von Optionen auf der Registerkarte "Zuordnung"](#mapping)  
  
-   [Festlegen der Optionen auf der Registerkarte "Erweitert"](#advanced)  
  
-   [Festlegen der Optionen im Dialogfeld "Verbindungs-Manager für DQS-Bereinigung"](#manager)  
  
##  <a name="open-the-dqs-cleansing-transformation-editor"></a><a name="open"></a> Öffnen des Transformations-Editors für die DQS-Bereinigung  
  
1.  Fügen Sie die DQS-Bereinigungstransformation dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]hinzu.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Komponente, und klicken Sie anschließend auf **Bearbeiten**.  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a>Festlegen von Optionen auf der Registerkarte "Verbindungs-Manager"  
 **Data Quality Services-Verbindungs-Manager**  
 Wählen Sie in der Liste einen vorhandenen DQS-Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Verbindungs-Manager für DQS-Bereinigung** einen neuen Verbindungs-Manager. Siehe [Festlegen der Optionen im Dialogfeld Verbindungs-Manager für DQS-Bereinigung](#manager)  
  
 **Data Quality-Wissensdatenbank**  
 Wählen Sie eine vorhandene DQS-Wissensdatenbank für die verbundene Datenquelle aus. Weitere Informationen zur DQS-Wissensdatenbank finden Sie unter [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Verbindung verschlüsseln**  
 Geben Sie an, ob die Verbindung verschlüsselt werden soll, um die Datenübertragung zwischen dem DQS- [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]Server und zu verschlüsseln.  
  
 **Verfügbare Domänen**  
 Listet die verfügbaren Domänen für die ausgewählte Wissensdatenbank auf. Es gibt zwei Typen von Domänen: einzelne Domänen und Verbunddomänen, die aus mindestens zwei einzelnen Domänen bestehen.  
  
 Weitere Informationen zum Zuordnen von Spalten zu Verbunddomänen finden Sie unter [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).  
  
 Weitere Informationen zu Domänen finden Sie unter [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Fehlerausgabe konfigurieren**  
 Gibt an, wie Fehler auf Zeilenebene verarbeitet werden. Wenn durch die Transformation Daten aus der verbundenen Datenquelle korrigiert werden, können aufgrund unerwarteter Datenwerte oder Überprüfungseinschränkungen Fehler auftreten.  
  
 Folgende Werte sind gültig:  
  
-   **Fehler bei Komponente**gibt an, dass die Transformation fehlgeschlagen ist und dass die Eingabedaten nicht in die Data Quality Services-Datenbank eingefügt werden. Dies ist der Standardwert.  
  
-   **Zeile umleiten**gibt an, dass die Eingabedaten nicht in die Data Quality Services-Datenbank eingefügt und an die Fehlerausgabe umgeleitet werden.  
  
##  <a name="set-options-on-the-mapping-tab"></a><a name="mapping"></a> Festlegen der Optionen auf der Registerkarte "Zuordnung"  
 Weitere Informationen zum Zuordnen von Spalten zu Verbunddomänen finden Sie unter [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).  
  
 **Verfügbare Eingabespalten**  
 Listet die Spalten aus der verbundenen Datenquelle auf. Wählen Sie Spalten aus, die zu korrigierende Daten enthalten.  
  
 **Eingabespalte**  
 Zeigt eine im Bereich **Verfügbare Eingabespalten** ausgewählte Eingabespalte an.  
  
 **Domäne**  
 Wählen Sie eine Domäne aus, die der Eingabespalte zugeordnet werden soll.  
  
 **Alias – Quelle**  
 Zeigt die Quellspalte an, die den ursprünglichen Spaltenwert enthält.  
  
 Klicken Sie in das Feld, um den Spaltennamen zu ändern.  
  
 **Ausgabealias**  
 Zeigt die Spalte an, die vom **Transformations-Editor für die DQS-Bereinigung**ausgegeben wird. Die Spalte enthält den ursprünglichen Spaltenwert oder den korrigierten Wert.  
  
 Klicken Sie in das Feld, um den Spaltennamen zu ändern.  
  
 **Alias – Status**  
 Zeigt die Spalte an, die Statusinformationen für die korrigierten Daten enthält. Klicken Sie in das Feld, um den Spaltennamen zu ändern.  
  
##  <a name="set-options-on-the-advanced-tab"></a><a name="advanced"></a>Festlegen von Optionen auf der Registerkarte "Erweitert"  
 **Ausgabe standardisieren**  
 Gibt an, ob die Daten im standardisierten Format auf Grundlage des für Domänen definierten Ausgabeformats ausgegeben werden. Weitere Informationen zum standardisierten Format finden Sie unter [Datenbereinigung](../../2014/data-quality-services/data-cleansing.md).  
  
 **Confidence**  
 Gibt an, ob der Vertrauensgrad für korrigierte Daten eingeschlossen wird. Der Vertrauensgrad gibt die DQS-Sicherheitsstufe der Korrektur oder des Vorschlags an. Weitere Informationen zu Vertrauensgraden finden Sie unter [Datenbereinigung](../../2014/data-quality-services/data-cleansing.md).  
  
 **Grund**  
 Gibt an, ob der Grund für die Datenkorrektur eingeschlossen wird.  
  
 **Angefügte Daten**  
 Gibt an, ob weitere, von einem vorhandenen Verweisdatenanbieter empfangene Daten ausgegeben werden. Weitere Informationen finden Sie unter [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md).  
  
 **Angefügtes Datenschema**  
 Gibt an, ob das Datenschema ausgegeben wird. Weitere Informationen finden Sie unter [Anfügen einer Domäne oder Verbund Domäne an Verweis Daten](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).  
  
##  <a name="set-the-options-in-the-dqs-cleansing-connection-manager-dialog-box"></a><a name="manager"></a>Festlegen der Optionen im Dialogfeld "Verbindungs-Manager für DQS-Bereinigung"  
 **Servername**  
 Wählen Sie den Namen des DQS-Servers aus, mit dem Sie eine Verbindung herstellen möchten, oder geben Sie ihn ein. Weitere Informationen zum Server finden Sie unter [DQS Administration](../../2014/data-quality-services/dqs-administration.md).  
  
 **Testen der Verbindung**  
 Klicken Sie auf diese Schaltfläche, um zu überprüfen, ob die angegebene Verbindung gültig ist.  
  
 Sie können das Dialogfeld **Verbindungs-Manager für DQS-Bereinigung** auch wie folgt über den Verbindungsbereich öffnen:  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ein vorhandenes [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, oder erstellen Sie ein neues Projekt.  
  
2.  Klicken Sie im Verbindungsbereich mit der rechten Maustaste auf **Neue Verbindung**, und klicken Sie anschließend auf **DQS**.  
  
3.  Klicken Sie auf **Hinzufügen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anwenden von Datenqualitätsregeln auf eine Datenquelle](data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  
