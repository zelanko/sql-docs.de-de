---
title: Aktionen (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- actions [Analysis Services]
- actions [Analysis Services], about actions
- MDX [Analysis Services], actions
- cubes [Analysis Services], actions
- OLAP objects [Analysis Services], actions
ms.assetid: 07229bb2-805c-427e-8455-69c9ca5d01e0
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e5828886d047c6b8fcec0d511a8d1ddbd94bbae5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150905"
---
# <a name="actions-analysis-services---multidimensional-data"></a>Aktionen (Analysis Services – Mehrdimensionale Daten)
  Aktionen können von verschiedenen Typen sein und müssen entsprechend erstellt werden. Folgende Aktionen stehen zur Verfügung:  
  
-   Drillthroughaktionen geben die Zeilen zurück, die die zugrunde liegenden Daten der ausgewählten Zellen des Cubes darstellen, in dem die Aktion ausgeführt wird.  
  
-   Berichtsaktionen geben einen Bericht von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zurück, der mit dem ausgewählten Abschnitt des Cubes verbunden ist, in dem die Aktion ausgeführt wird.  
  
-   Standardaktionen geben das Aktionselement zurück (URL, HTML, DataSet, RowSet und sonstige Elemente), das mit dem ausgewählten Abschnitt des Cubes verbunden ist, in dem die Aktion ausgeführt wird.  
  
 Von der Clientanwendung wird eine Abfrageschnittstelle wie ADOMD.NET verwendet, um die Aktionen abzurufen und für die Endbenutzer bereitzustellen. Weitere Informationen finden Sie unter [Entwickeln mit ADOMD.NET](adomd-net/developing-with-adomd-net.md).  
  
 Ein einfaches <xref:Microsoft.AnalysisServices.Action> -Objekt besteht aus: grundlegenden Informationen, dem Ziel, auf dem die Aktion ausgeführt werden soll, einer Bedingung, um den Aktionsbereich einzuschränken und dem Typ. Grundlegende Informationen beinhalten den Namen der Aktion, die Beschreibung der Aktion, die für die Aktion vorgeschlagene Beschriftung usw.  
  
 Das Ziel ist die eigentliche Position im Cube, wo die Aktion ausgeführt werden soll. Das Ziel besteht aus einem Zieltyp und einem Zielobjekt. Der Zieltyp stellt die Objektart im Cube dar, wo die Aktion aktiviert werden soll. Zieltyp können unter anderem Ebenenelemente, Zellen, Hierarchie und Hierarchieelemente sein. Das Zielobjekt ist ein spezifisches Objekt des Zieltyps. Wenn der Zieltyp "Hierarchie" ist, ist das Zielobjekt eine der definierten Hierarchien in dem Cube.  
  
 Die Bedingung ist ein `Boolean` MDX-Ausdruck, der beim Aktionsereignis ausgewertet wird. Wenn die Bedingung ergibt `true`, und klicken Sie dann die Aktion ausgeführt wird. Andernfalls wird die Aktion nicht ausgeführt.  
  
 Der Typ entspricht der Art der Aktion, die ausgeführt werden soll. <xref:Microsoft.AnalysisServices.Action> ist eine abstrakte Klasse. Sie müssen daher eine abgeleitete Klasse verwenden, um diese Klasse verwenden zu können. Zwei Arten von Aktionen werden vordefiniert: Drillthrough und Berichterstellung. Diese verfügen über entsprechende abgeleitete Klassen: <xref:Microsoft.AnalysisServices.DrillThroughAction> und <xref:Microsoft.AnalysisServices.ReportAction>. Andere Aktionen werden mit der <xref:Microsoft.AnalysisServices.StandardAction> -Klasse abgedeckt.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ist eine Aktion eine gespeicherte MDX-Anweisung, die Clientanwendungen angezeigt und von diesen verwendet werden kann. Eine Aktion ist also ein Clientbefehl, der auf dem Server definiert und gespeichert wird. Eine Aktion enthält auch Informationen, die angeben, wann und wie die MDX-Anweisung von der Clientanwendung angezeigt und verarbeitet werden soll. Durch den von der Aktion angegebenen Vorgang kann eine Anwendung (mithilfe der Informationen in der Aktion als Parameter) gestartet werden oder können Informationen basierend auf von der Aktion bereitgestellten Kriterien abgerufen werden.  
  
 Mithilfe von Aktionen können Anwender des Produkts im geschäftlichen Bereich auf die Ergebnisse ihrer Analysen reagieren. Das Speichern und Wiederverwenden von Aktionen erweitert die Möglichkeiten von Endbenutzern über die herkömmliche Analyse hinaus, die in der Regel mit der Darstellung der Daten endet, sodass sie Lösungen für entdeckte Probleme und Mängel initiieren und so die Business Intelligence-Anwendung über den Cube hinaus erweitern können. Mit Aktionen können Clientanwendungen von einem anspruchsvollen Tool für die Datendarstellung in einen wesentlichen Bestandteil des Unternehmensbetriebssystems umgewandelt werden. Statt sich auf das Senden von Daten als Eingabe an Betriebsanwendungen zu konzentrieren, können Endbenutzer beim Entscheidungsprozess "den Kreis schließen". Diese Möglichkeit, analytische Daten in Entscheidungen umzuwandeln, ist für die erfolgreiche Business Intelligence-Anwendung entscheidend.  
  
 Ein Anwender des Produkts im geschäftlichen Bereich, der einen Cube durchsucht, stellt z. B. fest, dass der aktuelle Bestand eines bestimmten Produkts niedrig ist. Die Clientanwendung stellt eine Liste mit Aktionen in Bezug auf den niedrigen Produktbestandwert bereit, die aus der Analysis Services-Datenbank abgerufen werden. Der Anwender des Produkts im geschäftlichen Bereich wählt die Order-Aktion für das Element des Cubes aus, das das Produkt darstellt. Mit der Order-Aktion wird eine neue Bestellung initiiert, indem eine gespeicherte Prozedur in der Betriebsdatenbank aufgerufen wird. Diese gespeicherte Prozedur generiert die entsprechenden Informationen, die an das Bestellungseingabesystem gesendet werden.  
  
 Sie können beim Erstellen von Aktionen flexibel vorgehen: Eine Aktion kann z. B. eine Anwendung starten oder Informationen aus einer Datenbank abrufen. Sie können eine Aktion so konfigurieren, dass sie von beinahe jedem Teil eines Cubes ausgelöst wird, einschließlich Dimensionen, Ebenen, Elementen und Zellen, oder Sie können mehrere Aktionen für denselben Teil eines Cubes erstellen. Sie können zudem Zeichenfolgenparameter an die aufgerufenen Anwendungen übergeben und die Aktionsbeschriftungen angeben, die für Endbenutzer angezeigt werden, wenn die Aktion ausgeführt wird.  
  
> [!IMPORTANT]  
>  Damit Anwender des Produkts im geschäftlichen Bereich Aktionen verwenden können, muss die vom Anwender verwendete Clientanwendung Aktionen unterstützen.  
  
## <a name="types-of-actions"></a>Aktionstypen  
 In der folgenden Tabelle werden die in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]enthaltenen Aktionstypen aufgeführt:  
  
|Aktionstyp|Description|  
|-----------------|-----------------|  
|CommandLine|Führt einen Befehl an der Eingabeaufforderung aus.|  
|Dataset|Gibt ein Dataset an eine Clientanwendung zurück.|  
|Drillthrough ausführen|Gibt eine Drillthroughanweisung als Ausdruck zurück, den der Client zur Rückgabe eines Rowsets ausführt.|  
|Html|Führt ein HTML-Skript in einem Internetbrowser aus.|  
|Proprietär|Führt einen Vorgang über eine Schnittstelle aus, die nicht in dieser Tabelle aufgelistet ist.|  
|Bericht|Übermittelt eine parametrisierte, URL-basierte Anforderung an einen Berichtsserver und gibt einen Bericht an eine Clientanwendung zurück.|  
|Rowset|Gibt ein Rowset an eine Clientanwendung zurück.|  
|Anweisung|Gibt einen OLE DB-Befehl zurück.|  
|URL|Zeigt eine dynamische Webseite in einem Internetbrowser an.|  
  
## <a name="resolving-and-executing-actions"></a>Auflösen und Ausführen von Aktionen  
 Wenn ein geschäftlicher Benutzer auf das Objekt zugreift, für das das Befehlsobjekt definiert ist, wird die der Aktion zugeordnete Anweisung automatisch aufgelöst, wodurch sie für die Clientanwendung verfügbar wird. Die Aktion wird jedoch nicht automatisch ausgeführt. Die Aktion wird nur ausgeführt, wenn der Anwender des Produkts im geschäftlichen Bereich einen clientspezifischen Vorgang ausführt, der die Aktion initiiert. Clientanwendungen können z. B. eine Liste mit Aktionen als Popupmenü anzeigen, wenn der Benutzer mit der rechten Maustaste auf ein bestimmtes Element bzw. eine Zelle klickt.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktionen in mehrdimensionalen Modellen](actions-in-multidimensional-models.md)  
  
  