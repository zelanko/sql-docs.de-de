---
title: Bezeichner (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- regular identifiers [Integration Services]
- variables [Integration Services], expressions
- identifiers [Integration Services]
- expressions [Integration Services], variables
- lineage identifiers
- columns [Integration Services], identifiers
- names [Integration Services]
- expressions [Integration Services], identifiers
- qualified identifiers [Integration Services]
ms.assetid: 56af984d-88b4-4db8-b6a2-6b07315a699e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a7913d82b471b50605c51fbfb61b3782cf135382
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62898858"
---
# <a name="identifiers-ssis"></a>Bezeichner (SSIS)
  In Ausdrücken sind Bezeichner Spalten und Variablen, die für den Vorgang verfügbar sind. Reguläre und qualifizierte Bezeichner können in Ausdrücken verwendet werden.  
  
## <a name="regular-identifiers"></a>Reguläre Bezeichner  
 Ein regulärer Bezeichner erfordert keine zusätzlichen Qualifizierer. Beispielsweise ist **MiddleName**ein regulärer Bezeichner. Dabei handelt es sich um eine Spalte in der **Contacts** -Tabelle der **AdventureWorks** -Datenbank.  
  
 Die Namen von regulären Bezeichnern müssen den folgenden Regeln entsprechen:  
  
-   Das erste Zeichen des Namens muss ein Buchstabe gemäß Unicode-Standard 2.0 sein oder ein Unterstrich (_).  
  
-   Nachfolgende Zeichen können Buchstaben oder Zahlen gemäß Unicode-Standard 2.0, ein Unterstrich (_) oder die Zeichen \@, $ und # sein.  
  
> [!IMPORTANT]  
>  Nur die aufgeführten eingebetteten Zeichen und Sonderzeichen sind in regulären Bezeichnern gültig. Für die Verwendung von Leerzeichen und Sonderzeichen müssen Sie anstelle eines regulären Bezeichners einen qualifizierten Bezeichner verwenden.  
  
## <a name="qualified-identifiers"></a>Qualifizierte Bezeichner  
 Ein qualifizierter Bezeichner wird durch eckige Klammern getrennt. Für einen Bezeichner kann ein Trennzeichen erforderlich sein, weil der Name des Bezeichners Leerzeichen einschließt oder weil das erste Zeichen des Bezeichnernamens kein Buchstabe oder ein Unterstrich ist. Beispielsweise muss der Spaltenname **Middle Name** mit eckigen Klammern qualifiziert und in einem Ausdruck als „[Middle Name]“ eingegeben werden.  
  
 Wenn der Name des Bezeichners Leerzeichen einschließt oder wenn der Name kein gültiger Name für einen regulären Bezeichner ist, muss der Bezeichner qualifiziert werden. Die Ausdrucksauswertung verwendet öffnende und schließende eckige Klammern ([]), um Bezeichner zu qualifizieren. Die eckigen Klammern befinden sich an der ersten und letzten Position der Zeichenfolge. Beispielsweise wird der Bezeichner 5$> zu [5$>]. Eckige Klammern können für Spaltennamen, Variablennamen und Funktionsnamen verwendet werden.  
  
 Falls Sie Ausdrücke mithilfe der Dialogfelder des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers erstellen, werden reguläre Bezeichner automatisch in eckige Klammern eingeschlossen. Eckige Klammern sind jedoch nur erforderlich, wenn der Name ungültige Zeichen enthält. Beispielsweise ist die Spalte mit dem Namen **MiddleName** auch ohne eckige Klammern gültig.  
  
 In Ausdrücken kann nicht auf Spaltennamen verwiesen werden, die eckige Klammern einschließen. Beispielsweise kann der Spaltenname **Column[1]** nicht in einem Ausdruck verwendet werden. Der Spaltenname müsste ansonsten in einen Ausdruck ohne eckige Klammern umbenannt werden.  
  
## <a name="lineage-identifiers"></a>Herkunftsbezeichner  
 In Ausdrücken kann mit Herkunftsbezeichnern auf Spalten verwiesen werden. Die Herkunftsbezeichner werden automatisch zugewiesen, wenn Sie das Paket erstellen. Den Herkunftsbezeichner für eine Spalte können Sie im **-Designer im Dialogfeld** Erweiterter Editor **auf der Registerkarte** Spalteneigenschaften [!INCLUDE[ssIS](../../includes/ssis-md.md)] anzeigen.  
  
 Wenn Sie mithilfe des Herkunftsbezeichners auf eine Spalte verweisen, muss der Bezeichner das Nummernzeichenpräfix (#) einschließen. Beispielsweise muss eine Spalte mit dem Herkunftsbezeichner 147 als #147 dargestellt werden.  
  
 Falls ein Ausdruck erfolgreich analysiert wird, ersetzt die Ausdrucksauswertung den Herkunftsbezeichner durch Spaltennamen im Dialogfeld.  
  
## <a name="unique-column-names"></a>Eindeutige Spaltennamen  
 Mehrere in einem Paket verwendete Komponenten können Spalten mit demselben Namen verfügbar machen. Falls diese Spalten in Ausdrücken verwendet werden, muss sichergestellt werden, dass sie nicht mehrdeutig sind, damit die Ausdrücke erfolgreich analysiert werden können. Die Ausdrucksauswertung unterstützt die punktierte Schreibweise zum Identifizieren der Spaltenquelle. Beispielsweise werden zwei Spalten mit dem Namen **Age** zu **FlatFileSource.Age** und **OLEDBSource.Age**. Daran ist erkennbar, dass FlatFileSource und OLEDBSource die Quellen sind. Der Parser behandelt den vollqualifizierten Namen als einen einzelnen Spaltennamen.  
  
 Die Namen von Spaltenkomponenten und Spalten werden separat qualifiziert. Die folgenden Beispiele veranschaulichen die gültige Verwendung von eckigen Klammern in einer gepunkteten Schreibweise:  
  
-   Der Name der Quellkomponente schließt Leerzeichen ein.  
  
    ```  
    [MySo urce].Age  
    ```  
  
-   Das erste Zeichen im Spaltennamen ist ungültig.  
  
    ```  
    MySource.[#Age]  
    ```  
  
-   Die Namen der Quellkomponente und der Spalte enthalten ungültige Zeichen.  
  
    ```  
    [MySource?].[#Age]  
    ```  
  
> [!IMPORTANT]  
>  Falls beide Elemente in gepunkteter Schreibweise in eckige Klammern eingeschlossen sind, interpretiert die Ausdrucksauswertung das Klammernpaar als einen einzelnen Bezeichner, und nicht als eine Kombination aus Quelle und Spalte.  
  
## <a name="variables-in-expressions"></a>Variablen in Ausdrücken  
 Wenn in Ausdrücken auf Variablen verwiesen wird, muss das \@-Präfix verwendet werden. Beispielsweise wird auf die **Counter**-Variable mit \@Counter verwiesen. Das Zeichen \@ ist nicht Bestandteil des Variablennamens, sondern identifiziert die Variable nur gegenüber der Ausdrucksauswertung. Wenn Sie Ausdrücke mithilfe der Dialogfelder des [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Designers erstellen, wird dem Variablennamen automatisch das \@-Zeichen hinzugefügt. Leerzeichen sind zwischen dem \@-Zeichen und dem Variablennamen nicht zulässig.  
  
 Für Variablennamen gelten dieselben Regeln wie für andere reguläre Bezeichner:  
  
-   Das erste Zeichen des Namens muss ein Buchstabe gemäß Unicode-Standard 2.0 sein oder ein Unterstrich (_).  
  
-   Nachfolgende Zeichen können Buchstaben oder Zahlen gemäß Unicode-Standard 2.0, ein Unterstrich (_) oder die Zeichen \@, $ und # sein.  
  
 Enthält ein Variablenname andere als die aufgeführten Zeichen, muss die Variable in eckige Klammern eingeschlossen werden. Beispielsweise müssen Variablennamen mit Leerzeichen in eckige Klammern eingeschlossen werden. Auf das \@-Zeichen folgt die öffnende eckige Klammer. Beispielsweise wird auf die **My Name**-Variable mit „\@[My Name]“ verwiesen. Leerzeichen sind zwischen dem Variablennamen und den eckigen Klammern nicht zulässig.  
  
> [!NOTE]  
>  Die Namen von benutzerdefinierten und Systemvariablen unterscheiden nach Groß-/Kleinschreibung.  
  
## <a name="unique-variable-names"></a>Eindeutige Variablennamen  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] unterstützt benutzerdefinierte Variablen und stellt eine Reihe von Systemvariablen bereit. Standardmäßig gehören benutzerdefinierte Variablen zum Namespace **User** und Systemvariablen zum Namespace **System** . Sie können zusätzliche Namespaces für benutzerdefinierte Variablen erstellen und die Namespacenamen entsprechend den Anforderungen Ihrer Anwendung aktualisieren. Im Ausdrucks-Generator werden bereichsinterne Variablen in allen Namespaces aufgeführt.  
  
 Alle Variablen weisen einen Bereich auf und gehören zu einem Namespace. Eine Variable weist einen Paketbereich oder den Bereich eines Containers oder Tasks im Paket auf. Im Ausdrucks-Generator des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers werden nur die bereichsinternen Variablen aufgeführt. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md) und [Verwenden von Variablen in Paketen](../use-variables-in-packages.md).  
  
 Für Variablen, die in Ausdrücken verwendet werden, sind eindeutige Namen erforderlich, damit die Ausdrucksauswertung den Ausdruck ordnungsgemäß auswertet. Falls ein Paket mehrere gleichnamige Variablen verwendet, müssen deren Namespaces unterschiedlich sein. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stellt einen Namespace-Auflösungsoperator bereit, bestehend aus zwei Doppelpunkten (::), um eine Variable mit ihrem Namespace zu qualifizieren. Beispielsweise verwenden die folgenden Ausdrücke zwei Variablen mit dem Namen **Count**. Eine Variable gehört zum Namespace **User** und die andere zum Namespace **MyNamespace** .  
  
```  
@[User::Count] > @[MyNamespace::Count]  
```  
  
> [!IMPORTANT]  
>  Sie müssen die Kombination aus Namespace und qualifiziertem Variablennamen in eckige Klammern einschließen, damit die Ausdrucksauswertung die Variable erkennt.  
  
 Wenn der Wert von **count** im **User** -Namespace 10 und der Wert von **count** in **MyNamespace** 2 ist, wird der Ausdruck als `true` ausgewertet, da die Ausdrucks Auswertung zwei unterschiedliche Variablen erkennt.  
  
 Wenn Variablennamen nicht eindeutig sind, wird kein Fehler gemeldet. Die Ausdrucksauswertung verwendet stattdessen nur eine Instanz der Variablen zum Auswerten des Ausdrucks und gibt ein falsches Ergebnis zurück. Beispielsweise war der folgende Ausdruck zum Vergleichen der Werte (10 und 2) für zwei separate **count** -Variablen vorgesehen. der Ausdruck wird jedoch `false` zu ausgewertet, da die Ausdrucks Auswertung dieselbe Instanz der **count** -Variablen zweimal verwendet.  
  
```  
@Count > @Count  
```  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), auf pragmaticworks.com  
  
  
