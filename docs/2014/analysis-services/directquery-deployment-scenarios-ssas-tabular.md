---
title: DirectQuery-Bereitstellungsszenarien (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 2aaf5cb8-294b-4031-94b3-fe605d7fc4c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 679658c7ffdc00a90cb485bb9f1892ddffde7775
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135180"
---
# <a name="directquery-deployment-scenarios-ssas-tabular"></a>DirectQuery-Bereitstellungsszenarien (SSAS – tabellarisch)
  In diesem Abschnitt wird eine exemplarische Vorgehensweise des Entwurfs- und Bereitstellungsprozesses für DirectQuery-Modelle erläutert. Sie können DirectQuery konfigurieren, um ausschließlich relationale Daten (nur DirectQuery) zu verwenden, oder Sie können das Modell konfigurieren, um zwischen der Verwendung ausschließlich zwischengespeicherter Daten oder ausschließlich relationaler Daten zu wechseln (hybrider Modus). In diesem Abschnitt wird der Implementierungsprozess für beide Modi erläutert. Außerdem werden mögliche Unterschiede bei den Abfrageergebnissen in Abhängigkeit vom Modus und der Sicherheitskonfiguration beschrieben.  
  
 [Entwurfs- und Bereitstellungsschritte](#bkmk_DQProcedure)  
  
 [Vergleichen von DirectQuery-Konfigurationen](#bkmk_Configurations)  
  
##  <a name="bkmk_DQProcedure"></a> Entwurfs- und Bereitstellungsschritte  
 **Schritt 1. Erstellen Sie die Projektmappe**  
  
 Unabhängig vom verwendeten Modus müssen Sie die Informationen überprüfen, in denen Einschränkungen hinsichtlich der Daten, die in DirectQuery-Modellen verwendet werden können, beschrieben werden. Alle im Modell verwendeten Daten und Berichte müssen z. B. von einer einzelnen SQL Server-Datenbank kommen. Weitere Informationen finden Sie unter [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](tabular-models/directquery-mode-ssas-tabular.md).  
  
 Überprüfen Sie außerdem die Einschränkungen bezüglich der Measures und der berechneten Spalten. Stellen Sie fest, ob die Formeln, die Sie zu verwenden beabsichtigen, mit dem DirectQuery-Modus kompatibel sind. Sie müssen unter Umständen die folgenden Elemente entfernen oder ändern:  
  
-   Berechnete Spalten werden nicht unterstützt.  
  
-   Kopierte und eingefügte Daten können nicht verwendet werden. Wenn Sie ein PowerPivot-Modell importieren, um die Lösung zu beschleunigen, müssen Sie sicherstellen, das verknüpfte Tabellen vor dem Importieren der Lösung gelöscht werden, da die entsprechenden Daten nicht gelöscht werden können und eventuell die DirectQuery-Überprüfung blockieren.  
  
 **Schritt 2. Aktivieren des DirectQuery-Modus im Modell-designer**  
  
 Standardmäßig wird DirectQuery deaktiviert. Daher müssen Sie die Entwurfsumgebung für die Unterstützung des DirectQuery-Modus konfigurieren.  
  
 Mit der rechten Maustaste die **Model.bim** Knoten im Projektmappen-Explorer, und legen Sie die Eigenschaft **DirectQuery-Modus**zu `On`.  
  
 Sie können DirectQuery jederzeit aktivieren. Damit jedoch keine Spalten oder Formeln erstellt werden, die mit dem DirectQuery-Modus nicht kompatibel sind, wird empfohlen, den DirectQuery-Modus von Anfang an zu aktivieren.  
  
 Zunächst werden selbst die DirectQuery-Modelle immer im Arbeitsspeicher erstellt. Der Standardabfragemodus für die Arbeitsbereichsdatenbank wird ebenfalls auf **DirectQuery mit InMemory**festgelegt. Mit diesem hybriden Arbeitsmodus können Sie während des Modellentwurfsprozesses den Cache der importierten Daten zugunsten einer verbesserten Leistung verwenden, während das Modell gegen DirectQuery-Anforderungen überprüft wird.  
  
 **Schritt 3. Beheben von Validierungsfehlern**  
  
 Wenn Sie beim Aktivieren von DirectQuery Validierungsfehler erhalten, oder wenn Sie neue Daten oder Formeln hinzufügen, öffnen Sie die **Visual Studio-Fehlerliste**, und führen dann die erforderlichen Aktionen aus.  
  
-   Ändern Sie alle erforderlichen Eigenschafteneinstellungen für den DirectQuery-Modus entsprechend der Beschreibung in den Fehlermeldungen.  
  
-   Entfernen Sie berechnete Spalten. Wenn Sie für ein bestimmtes Measure eine berechnete Spalte benötigen, können Sie immer die Spalte erstellen, mit der [relationale Abfrage-Designer &#40;SSAS&#41; ](relational-query-designer-ssas.md) im Tabellenimport-Assistenten bereitgestellt.  
  
-   Ändern oder entfernen Sie Formeln, die mit dem DirectQuery-Modus nicht kompatibel sind. Wenn Sie eine bestimmte Funktion für eine Berechnung benötigen, prüfen Sie Methoden zur Bereitstellung eines Äquivalents mithilfe von Transact-SQL.  
  
-   Fügen Sie Daten nach Bedarf hinzu.  Wenn das Modell zuvor kopierte und eingefügte Daten oder Daten von anderen Anbietern als dem SQL Server verwendet hat, können Sie neue Sichten und abgeleitete Spalten innerhalb der vorhandenen Verbindung erstellen oder verteilte Abfragen verwenden.  Alle in einem DirectQuery-Modell verwendeten Daten müssen über eine einzelne SQL Server-Datenquelle zugänglich sein.  
  
 **Schritt 4. Festlegen der bevorzugten Methode zur Beantwortung von Abfragen für das Modell**  
  
|||  
|-|-|  
|**Nur DirectQuery**|Legen Sie die Eigenschaft auf **DirectQuery**fest.|  
|**Hybridmodus**|Legen Sie die Eigenschaft auf **InMemory mit DirectQuery** oder **DirectQuery mit InMemory**fest.<br /><br /> Sie können diesen Wert zu einem späteren Zeitpunkt ändern, um eine andere Einstellung zu verwenden.<br /><br /> Beachten Sie, dass Clients die bevorzugte Methode in der Verbindungszeichenfolge überschreiben können.|  
  
 **Schritt 5. Angeben der DirectQuery-partition**  
  
|||  
|-|-|  
|**Nur DirectQuery**|Optional. Bei einem ausschließlichen DirectQuery-Modell besteht keine Notwendigkeit einer Partition.<br /><br /> Wenn Sie jedoch während der Entwurfsphase Partitionen im Modell erstellen, müssen Sie beachten, dass nur eine Partition als Datenquelle verwendet werden kann. Standardmäßig wird die erste Partition, die Sie erstellen, als DirectQuery-Partition verwendet.<br /><br /> Um zu gewährleisten, dass alle vom Modell benötigten Daten über die DirectQuery-Partition verfügbar sind, wählen Sie eine DirectQuery-Partition und bearbeiten Sie die SQL-Anweisung, um das gesamte Dataset abzurufen.|  
|**Hybridmodus**|Wenn eine Tabelle im Modell mehrere Partitionen aufweist, müssen Sie eine einzelne Partition als *DirectQuery-Partition*auswählen. Wenn Sie standardmäßig keine Partition zuweisen, wird die erste erstellte Partition als DirectQuery-Partition verwendet.<br /><br /> Legen Sie Verarbeitungsoptionen für alle Partitionen mit Ausnahme von DirectQuery fest. In der Regel wird die DirectQuery-Partition nie verarbeitet, da die Daten von der relationalen Quelle aus übergeben werden.<br /><br /> Weitere Informationen finden Sie unter [Partitionen und DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](tabular-models/define-partitions-in-directquery-models-ssas-tabular.md).|  
  
 **Schritt 6. Identitätswechselinformationen**  
  
 Identitätswechsel wird nur für DirectQuery-Modelle unterstützt. Die Identitätswechseloption, **Identitätswechseleinstellungen**, definiert die Anmeldeinformationen, die verwendet werden, wenn Daten von der angegebenen SQL Server-Datenquelle angezeigt werden.  
  
|||  
|-|-|  
|**Nur DirectQuery**|Geben Sie für die Eigenschaft  **Identitätswechseleinstellungen** das Konto an, mit dem eine Verbindung mit der SQL Server-Datenquelle hergestellt werden soll.<br /><br /> Wenn Sie den Wert des verwenden **ImpersonateCurrentUser**, die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dass Hosts das Modell die Anmeldeinformationen des aktuellen Benutzers des Modells zu SQL Server-Datenbank erfolgreich abgeschlossen werden.|  
|**Hybridmodus**|Geben Sie für die Eigenschaft **Identitätswechseleinstellungen** das Konto an, mit dem auf die Daten der SQL Server-Datenquelle zugegriffen werden soll.<br /><br /> Diese Einstellung beeinflusst nicht die Anmeldeinformationen, die zum Verarbeiten des vom Modell verwendeten Caches verwendet werden.|  
  
 **Schritt 7 fort. Bereitstellen des Modells**  
  
 Wenn Sie zum Bereitstellen des Modells bereit sind, öffnen Sie die **Projekt** Menü von Visual Studio, und wählen Sie **Eigenschaften**. Legen Sie die **QueryMode** -Eigenschaft auf einen der Werte fest, der in der folgenden Tabelle beschrieben wird:  
  
 Weitere Informationen finden Sie unter [Bereitstellen von SQL Server Data Tools &#40;SSAS – tabellarisch&#41;](tabular-models/deploy-from-sql-server-data-tools-ssas-tabular.md).  
  
|||  
|-|-|  
|**Nur DirectQuery**|**DirectQueryOnly**<br /><br /> Da Sie nur "Direkte Abfrage" angegeben haben, werden die Metadaten des Modells auf dem Server bereitgestellt, das Modell wird jedoch nicht verarbeitet.<br /><br /> Beachten Sie, dass der von der Arbeitsbereichsdatenbank verwendete Cache nicht automatisch gelöscht wird. Wenn Sie sicherstellen möchten, dass die zwischengespeicherten Daten für Benutzer nicht sichtbar sind, können Sie den Entwurfszeitcache löschen. Weitere Informationen finden Sie unter [deaktivieren Sie die Analysis Services Caches](instances/clear-the-analysis-services-caches.md).|  
|**Hybridmodus**|**DirectQuery mit InMemory**<br /><br /> **InMemory mit DirectQuery**<br /><br /> Beide Werte ermöglichen je nach Bedarf entweder die Verwendung des Caches oder der relationalen Datenquelle. Durch die Reihenfolge wird definiert, welche Datenquelle standardmäßig verwendet wird, wenn Abfragen für das Modell beantwortet werden.<br /><br /> Im Hybridmodus muss die Verarbeitung des Caches zur gleichen Zeit wie die Bereitstellung der Modellmetadaten auf dem Server stattfinden.<br /><br /> Sie können diese Einstellung nach der Bereitstellung ändern.|  
  
 **Schritt 8. Überprüfen des bereitgestellten Modells**  
  
 Öffnen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], in der Sie das Modell bereitgestellt haben. Klicken Sie mit der rechten Maustaste auf den Namen der Datenbank, und wählen Sie **Eigenschaften**aus.  
  
-   Die Eigenschaft **DirectQueryMode**wurde festgelegt, als die Bereitstellungseigenschaften definiert wurden.  
  
-   Die Eigenschaft **Identitätswechselinformationen der Datenquelle**wurde festgelegt, als die Benutzeridentitätswechseloptionen definiert wurden. Weitere Informationen finden Sie unter [Festlegen von Identitätswechseloptionen &#40;SSAS – mehrdimensional&#41;](multidimensional-models/set-impersonation-options-ssas-multidimensional.md).  
  
-   Sie können diese Eigenschaften nach der Bereitstellung des Modells jederzeit ändern.  
  
##  <a name="bkmk_Configurations"></a> Vergleichen von DirectQuery-Optionen  
 **Nur DirectQuery**  
 Diese Option wird bevorzugt, wenn Sie eine einzelne Datenquelle garantieren möchten oder wenn die Datenmenge die Größe des Arbeitsspeichers übersteigt. Wenn Sie mit einer sehr großen relationalen Datenquelle arbeiten, können Sie während der Entwurfszeit das Modell mit einer Teilmenge der Daten erstellen. Wenn Sie das Modell im ausschließlichen DirectQuery-Modus bereitstellen, können Sie die Datenquellendefinition bearbeiten, um alle erforderlichen Daten einzuschließen.  
  
 Diese Option wird auch bevorzugt, wenn Sie die von der relationalen Datenquelle bereitgestellten Sicherheitsfunktionen für die Steuerung des Benutzerzugriffs auf Daten verwenden möchten. Mit zwischengespeicherten tabellenmodellen können Sie auch [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Rollen zum Steuern des Datenzugriffs, aber die im Cache gespeicherten Daten müssen ebenfalls gesichert werden. Sie sollten diese Option immer verwenden, wenn der Sicherheitskontext erfordert, dass Daten niemals zwischengespeichert werden sollen.  
  
 In der folgenden Tabelle werden die möglichen Bereitstellungsergebnisse für den ausschließlichen DirectQuery-Modus beschrieben:  
  
|||  
|-|-|  
|**DirectQuery ohne cache**|Es werden keine Daten in den Zwischenspeicher geladen. Das Modell kann niemals verarbeitet werden.<br /><br /> Das Modell kann nur mit Clients abgerufen werden, die Unterstützung für DAX-Abfragen bieten. Abfrageergebnisse werden immer von der ursprünglichen Datenquelle zurückgegeben.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **DirectQuery**|  
|**DirectQuery mit Abfragen für Cache nur**|Bereitstellungsfehler Diese Konfiguration wird nicht unterstützt.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **In-Memory**|  
  
 **Hybridmodus**  
 Die Bereitstellung des Modells in einem Hybridmodus hat viele Vorteile: Sie können aktuelle Daten aus der SQL Server-Datenquelle nach Bedarf abrufen, doch die Beibehaltung des Caches bietet die Möglichkeit, mit Daten im Arbeitsspeicher zu arbeiten, um beim Entwerfen von Berichten oder Testen des Modells eine höhere Leistung zu erzielen.  
  
 Ein hybrider DirectQuery-Modus ist auch sinnvoll, wenn das Modell sehr groß ist. Damit Benutzer keine veralteten Daten erhalten oder das Modell nicht während der Verarbeitung des Caches nicht verfügbar ist, können Sie das Modell direkt auf den DirectQuery-Modus umstellen, während die Verarbeitung läuft. Die Leistung kann dadurch leicht beeinträchtigt werden, doch Daten können direkt vom relationalen Speicher abgerufen werden, wodurch sichergestellt wird, dass die Ergebnisse aktuell waren.  
  
 In der folgenden Tabelle wird das Bereitstellungsergebnis in jeder Kombination der DirectQuery-Optionen verglichen.  
  
|||  
|-|-|  
|**Hybridmodus mit Cache bevorzugt**|Das Modell kann verarbeitet werden, und Daten können in den Cache geladen werden. Bei Abfragen wird der Cache standardmäßig verwendet.  Wenn ein Client die DirectQuery-Quelle verwenden möchte, muss ein Parameter in die Verbindungszeichenfolge eingefügt werden.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **In-Memory with DirectQuery**|  
|**Hybridmodus mit DirectQuery bevorzugt**|Das Modell wird verarbeitet, und Daten können in den Cache geladen werden. Für Abfragen wird jedoch standardmäßig DirectQuery verwendet. Wenn ein Client die zwischengespeicherten Daten verwenden möchte, muss ein Parameter in die Verbindungszeichenfolge eingefügt werden. Wenn die Tabellen im Modell partitioniert werden, wird die Prinzipalpartition des Caches auch auf **InMemory mit DirectQuery**festgelegt.<br /><br /> **DirectQueryMode** = `On`<br /><br /> **QueryMode** = **DirectQuery mit InMemory**|  
  
## <a name="see-also"></a>Siehe auch  
 [DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [Zugriff auf Daten im tabellarischen Modell](tabular-models/tabular-model-data-access.md)  
  
  
