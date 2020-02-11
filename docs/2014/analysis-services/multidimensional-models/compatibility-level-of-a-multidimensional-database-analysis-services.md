---
title: Festlegen des Kompatibilitäts Grad einer mehrdimensionalen Datenbank (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c5eedfb396b33d33ceb9fbfad0245c4eb730997
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076690"
---
# <a name="set-the-compatibility-level-of-a-multidimensional-database-analysis-services"></a>Festlegen des Kompatibilitätsgrads einer mehrdimensionalen Datenbank (Analysis Services)
  In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]wird die Funktionsebene einer Datenbank durch die Eigenschaft „Datenbank-Kompatibilitätsgrad“ bestimmt. Kompatibilitätsgrade sind für jeden Modelltyp spezifisch. Beispielsweise hat ein Kompatibilitäts Grad `1100` von eine andere Bedeutung, je nachdem, ob die Datenbank mehrdimensional oder tabellarisch ist.  
  
 In diesem Thema wird nur der Kompatibilitätsgrad für mehrdimensionale Datenbanken beschrieben. Weitere Informationen zu tabellarischen Lösungen finden Sie unter [Kompatibilitäts Grad &#40;SSAS-tabellarischen SP1-&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
> [!NOTE]  
>  Tabellarische Modelle verfügen über zusätzliche Datenbank-Kompatibilitätsgrade, die für mehrdimensionale Modelle nicht gelten. Bei mehrdimensionalen Modellen gibt es keinen Kompatibilitätsgrad `1103`. Weitere Informationen `1103` zu tabellarischen Lösungen finden Sie [unter Neuerungen beim tabellarischen Modell in SQL Server 2012 SP1 und Kompatibilitäts Grad](https://go.microsoft.com/fwlink/?LinkId=301727) .  
  
 **Kompatibilitäts Grade für mehrdimensionale Datenbanken**  
  
 Das einzige Verhalten mehrdimensionaler Datenbanken, das derzeit im Hinblick auf die Funktionsebene abweicht, ist die Zeichenfolgenspeicherarchitektur. Wenn Sie den Kompatibilitätsgrad einer Datenbank erhöhen, können Sie den Höchstwert von 4 GB für den Zeichenfolgenspeicher überschreiben, in dem Measures und Dimensionen gespeichert sind.  
  
 Bei einer mehrdimensionalen Datenbank lauten die gültigen Werte für die `CompatibilityLevel`-Eigenschaft wie folgt:  
  
|Einstellung|BESCHREIBUNG|  
|-------------|-----------------|  
|`1050`|Dieser Wert ist in Skripts oder Tools nicht sichtbar, entspricht aber Datenbanken, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]oder [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]erstellt wurden. Alle Datenbanken, für die `CompatibilityLevel` nicht explizit festgelegt wurde, werden implizit mit Grad `1050` ausgeführt.|  
|`1100`|Dies ist der Standardwert für neue Datenbanken, die Sie in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]erstellen. Sie können diesen auch für Datenbanken angeben, die in früheren Versionen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt wurden, um die Verwendung von Funktionen zu ermöglichen, die nur unter diesem Kompatibilitätsgrad unterstützt werden (d. h., größerer Zeichenfolgenspeicher für Dimensionsattribute oder Distinct Count Measures, die Zeichenfolgendaten enthalten).<br /><br /> Datenbanken, die `CompatibilityLevel` über eine `1100` -Eigenschaft verfügen, `StringStoresCompatibilityLevel`um eine zusätzliche Eigenschaft () zu erhalten, mit der Sie alternativen Zeichen folgen Speicher für Partitionen und Dimensionen auswählen können.|  
  
> [!WARNING]  
>  Das Festlegen der Datenbankkompatibilität auf einen höheren Grad ist nicht umkehrbar. Nachdem Sie den Kompatibilitäts Grad auf `1100`erhöht haben, müssen Sie die Datenbank auf neueren Servern weiter ausführen. Ein Rollback auf `1050`ist nicht möglich. Eine `1100` -Datenbank kann nicht auf einer Server Version, die älter als [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ist, angefügt oder wieder hergestellt werden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Datenbank-Kompatibilitätsgrade werden mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eingeführt. Sie müssen über [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder höher verfügen, um den Datenbank-Kompatibilitätsgrad anzuzeigen oder festzulegen.  
  
 Die Datenbank darf kein lokaler Cube sein. Lokale Cubes bieten keine Unterstützung für die `CompatibilityLevel`-Eigenschaft.  
  
 Die Datenbank muss in einer früheren Version (SQL Server 2008 R2 oder früher) erstellt worden und dann an einen Server der Version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder höher angefügt oder dort wiederhergestellt worden sein. Für SQL Server 2012 bereitgestellte Datenbanken verfügen bereits über `1100` und können nicht zur Ausführung unter einem niedrigeren Grad herabgestuft werden.  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a>Bestimmen des bestehenden Datenbank-Kompatibilitätsgrads für eine mehrdimensionale Datenbank  
 XMLA ist die einzige Möglichkeit, den Datenbank-Kompatibilitätsgrad anzuzeigen oder zu ändern. Das XMLA-Skript, durch das die Datenbank in SQL Server Management Studio angegeben wird, kann angezeigt oder geändert werden.  
  
 Wenn Sie die XMLA-Definition einer Datenbank nach der `CompatibilityLevel`-Eigenschaft durchsuchen, diese aber nicht vorhanden ist, verfügt die Datenbank höchstwahrscheinlich über den Kompatibilitätsgrad `1050`.  
  
 Anweisungen zum Anzeigen und Ändern des XMLA-Skripts finden Sie im nächsten Abschnitt.  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a>Festlegen des Datenbank-Kompatibilitätsgrads in SQL Server Management Studio  
  
1.  Bevor Sie den Kompatibilitätsgrad erhöhen, sollten Sie die Datenbank sichern, damit Änderungen später bei Bedarf rückgängig gemacht werden können.  
  
2.  Stellen Sie mit SQL Server Management Studio eine Verbindung mit dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server her, der die Datenbank hostet.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Datenbanknamen, zeigen Sie auf **Skript für Datenbank als**, zeigen Sie auf **ALTER in**, und wählen Sie dann **Neues Abfrage-Editor-Fenster**aus. Eine XMLA-Darstellung der Datenbank wird in einem neuen Fenster geöffnet.  
  
4.  Kopieren Sie das folgende XML-Element:  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  Fügen Sie es nach dem schließenden `</Annotations>` -Element und vor dem `<Language>` -Element ein. Die XML sollte ähnlich wie im folgenden Beispiel aussehen:  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  Speichern Sie die Datei .  
  
7.  Klicken Sie zum Ausführen des Skripts im Menü Abfrage auf **Ausführen** , oder drücken Sie F5.  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a>Unterstützte Vorgänge, die denselben Kompatibilitätsgrad erfordern  
 Die folgenden Vorgänge erfordern, dass die Quelldatenbanken denselben Kompatibilitätsgrad verwenden.  
  
1.  Das Zusammenführen von Partitionen aus verschiedenen Datenbanken wird nur unterstützt, wenn beide Datenbanken denselben Kompatibilitätsgrad verwenden.  
  
2.  Für die Verwendung verknüpfter Dimensionen aus einer anderen Datenbank ist derselbe Kompatibilitätsgrad erforderlich. Wenn Sie z. b. eine verknüpfte [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Dimension aus einer Datenbank in einer [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Datenbank verwenden möchten, müssen Sie [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] die Datenbank auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] einen Server portieren und den Kompatibilitäts Grad auf `1100`festlegen.  
  
3.  Das Synchronisieren von Servern wird nur für Server unterstützt, die dieselbe Version und denselben Datenbank-Kompatibilitätsgrad verwenden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nachdem Sie den Datenbank-Kompatibilitätsgrad erhöht haben, können Sie die `StringStoresCompatibilityLevel`-Eigenschaft in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] festlegen. Dadurch wird der Zeichenfolgenspeicher für Measures und Dimensionen vergrößert. Weitere Informationen zu dieser Funktion finden Sie unter [Konfigurieren des Zeichenfolgenspeichers für Dimensionen und Partitionen](configure-string-storage-for-dimensions-and-partitions.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
