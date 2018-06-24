---
title: Integration Services-Variablen (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Integration Services], passing between packages
- user-defined variables [Integration Services]
- scope [Integration Services]
- system variables [Integration Services]
- variables [Integration Services]
- variables [Integration Services], about variables
- values [Integration Services]
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b6a5737635ffd69a7d09a93ac1104a1ee65b8277
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058101"
---
# <a name="integration-services-ssis-variables"></a>Integration Services-Variablen (SSIS)
  Variablen speichern Werte, die von einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket und dessen Containern, Tasks und Ereignishandlern zur Laufzeit verwendet werden können. Die Skripts im Skripttask und die Skriptkomponente können ebenfalls Variablen verwenden. Die Rangfolgeneinschränkungen, mit denen Tasks und Container zu einem Workflow zusammengestellt werden, können Variablen verwenden, wenn ihre Einschränkungsdefinitionen Ausdrücke einschließen.  
  
 Variablen in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen können für folgende Zwecke verwendet werden:  
  
-   Aktualisieren der Eigenschaften von Paketelementen zur Laufzeit. Beispielsweise können Sie die von einem Foreach-Schleifencontainer zulässige Anzahl von gleichzeitig ausführbaren Dateien dynamisch festlegen.  
  
-   Einschließen einer Nachschlagetabelle im Arbeitsspeicher. Beispielsweise kann von einem Paket ein Task SQL ausführen ausgeführt werden, der eine Variable mit Datenwerten lädt.  
  
-   Laden von Variablen mit Datenwerten und anschließend mit deren Hilfe Angeben einer Suchbedingung in einer WHERE-Klausel. Beispielsweise kann das Skript eines Skripttasks den Wert einer Variablen aktualisieren, die von einer Transact-SQL-Anweisung in einem Task SQL ausführen verwendet wird.  
  
-   Laden einer Variablen mit einer ganzen Zahl und anschließend Steuern der Schleifen in einer Paketablaufsteuerung mithilfe dieses Werts. Beispielsweise können Sie im Auswertungsausdruck eines For-Schleifencontainers die Iteration mithilfe einer Variablen steuern.  
  
-   Auffüllen von Parameterwerten für Transact-SQL-Anweisungen zur Laufzeit. Beispielsweise kann ein Paket einen Task SQL ausführen ausführen und anschließend die Parameter einer Transact-SQL-Anweisung mithilfe von Variablen dynamisch festlegen.  
  
-   Erstellen von Ausdrücken, die Variablenwerte einschließen. Beispielsweise kann die Transformation für abgeleitete Spalten eine Spalte mit dem Ergebnis aus dem Multiplizieren eines Variablenwerts mit einem Spaltenwert auffüllen.  
  
## <a name="system-and-user-defined-variables"></a>Systemvariablen und benutzerdefinierte Variablen  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] unterstützt zwei Arten von Variablen: Benutzerdefinierte Variablen und Systemvariablen. Benutzerdefinierte Variablen werden von Paketentwicklern definiert, und Systemvariablen werden von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]definiert. Sie können so viele benutzerdefinierte Variablen erstellen, wie für das Paket erforderlich sind. Zusätzliche Systemvariablen können jedoch nicht erstellt werden.  
  
 Alle Variablen, seien es Systemvariablen oder benutzerdefinierte Variablen, können in den Parameterbindungen verwendet werden, die der Task SQL ausführen zum Zuordnen von Variablen zu Parametern in SQL-Anweisungen verwendet. Weitere Informationen finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md) und [Parameter und Rückgabecodes im Task „SQL ausführen“](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
> [!NOTE]  
>  Bei den Namen von benutzerdefinierten und Systemvariablen wird nach Groß-/Kleinschreibung unterschieden.  
  
 Sie können benutzerdefinierte Variablen für alle [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Containertypen erstellen: Pakete, Foreach-Schleifencontainer, For-Schleifencontainer, Sequenzcontainer, Tasks und Ereignishandler. Bei benutzerdefinierten Variablen handelt es sich um Elemente der Variables-Auflistung des Containers.  
  
 Wenn Sie das Paket mit dem [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer erstellen, können Sie die Elemente der **Variables** -Auflistung im Ordner Variablen auf der Registerkarte **Paket-Explorer** des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers anzeigen. Die Ordner listen benutzerdefinierte Variablen und Systemvariablen auf.  
  
 Es gibt folgende Möglichkeiten, um benutzerdefinierte Variablen zu konfigurieren:  
  
-   Geben Sie einen Namen und eine Beschreibung für die Variable an.  
  
-   Geben Sie einen Namespace für die Variable an.  
  
-   Geben Sie an, ob die Variable ein Ereignis auslöst, wenn ihr Wert geändert wird.  
  
-   Geben Sie an, ob die Variable schreibgeschützt ist oder Lese-/Schreibzugriff aufweist.  
  
-   Verwenden Sie das Auswertungsergebnis eines Ausdrucks zum Festlegen des Variablenwerts.  
  
-   Erstellen Sie die Variable im Bereich des Pakets oder eines Paketobjekts, wie z. B. eines Tasks.  
  
-   Geben Sie den Wert und den Datentyp der Variablen an.  
  
 Die einzige konfigurierbare Option für Systemvariablen ist das Angeben, ob sie ein Ereignis auslösen, wenn sich der Wert ändert.  
  
 Ein anderer Systemvariablensatz ist für andere Containertypen verfügbar. Weitere Informationen zu den Systemvariablen, die von Paketen und deren Elementen verwendet werden, finden Sie unter [Systemvariablen](system-variables.md).  
  
 Weitere Informationen zu Szenarien für die Verwendung von Variablen in der Praxis finden Sie unter [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md).  
  
## <a name="variable-properties"></a>Variableneigenschaften  
 Sie können benutzerdefinierte Variablen konfigurieren, indem Sie die folgenden Eigenschaften im Fenster **Variablen** oder im Fenster **Eigenschaften** festlegen. Bestimmte Eigenschaften sind nur im Eigenschaftenfenster verfügbar.  
  
> [!NOTE]  
>  Die einzige konfigurierbare Option für Systemvariablen ist das Angeben, ob sie ein Ereignis auslösen, wenn sich der Wert ändert.  
  
 Description  
 Gibt die Beschreibung der Variablen an.  
  
 EvaluateAsExpression  
 Wenn die Eigenschaft auf festgelegt ist `True`, der Ausdruck wird verwendet, um den Wert der Variablen festgelegt.  
  
 expression  
 Gibt den der Variablen zugeordneten Ausdruck an.  
  
 Name  
 Gibt den Variablennamen an.  
  
 Namespace  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt zwei Namespaces bereit: **User** und **System**. Standardmäßig gehören benutzerdefinierte Variablen zum Namespace **User** und Systemvariablen zum Namespace **System** . Sie können zusätzliche Namespaces für benutzerdefinierte Variablen erstellen und den Namen des **User**-Namespaces ändern. Es ist jedoch nicht möglich, den Namen des **System**-Namespaces zu ändern, dem **System**-Namespace Variablen hinzuzufügen oder Systemvariablen einem anderen Namespace zuzuweisen.  
  
 RaiseChangedEvent  
 Wenn die Eigenschaft auf `True` festgelegt wird, wird das `OnVariableValueChanged`-Ereignis bei einer Änderung des Variablenwerts ausgelöst.  
  
 ReadOnly  
 Wenn die Eigenschaft auf `False` festgelegt wird, ist die Variable read\write.  
  
 Bereich  
 > [!NOTE]  
>  Sie können diese Eigenschafteneinstellung nur ändern, indem Sie im Fenster **Variablen** auf **Variable verschieben** klicken.  
  
 Eine Variable wird im Bereich eines Pakets oder im Bereich eines Containers, Tasks oder Ereignishandlers im Paket erstellt. Der Paketcontainer befindet sich ganz oben in der Containerhierarchie. Deshalb verhalten sich Variablen mit Paketbereichsfunktion wie globale Variablen und können von allen Containern im Paket verwendet werden. Entsprechend können Variablen, die im Bereich eines Containers definiert sind, wie z. B. eines For-Schleifencontainers, von allen Tasks oder Containern innerhalb des For-Schleifencontainers verwendet werden.  
  
 Falls ein Paket mithilfe des Tasks Paket ausführen andere Pakete ausführt, können die Variablen, die im Bereich des aufrufenden Pakets oder des Tasks Paket ausführen definiert sind, dem aufgerufenen Paket mithilfe des Konfigurationstyps Variable für das übergeordnete Paket zur Verfügung gestellt werden. Weitere Informationen finden Sie unter [Package Configurations](../../2014/integration-services/package-configurations.md).  
  
 IncludeInDebugDump  
 Geben Sie an, ob der Variablenwert in den Debugdumpdateien enthalten ist.  
  
 Für benutzerdefinierte Variablen und Systemvariablen, der Standardwert für die **InclueInDebugDump** Option ist `true`.  
  
 Für benutzerdefinierte Variablen setzt das System jedoch den **IncludeInDebugDump** option `false` Wenn die folgenden Bedingungen erfüllt sind:  
  
-   Wenn die **EvaluateAsExpression** Variable als Eigenschaft festgelegt ist, um `true`, setzt das System die **IncludeInDebugDump** option `false`.  
  
     Um den Text des Ausdrucks als Variablenwert in den debugdumpdateien aufzunehmen, legen Sie die **IncludeInDebugDump** option `true`.  
  
-   Wenn der Datentyp der Variablen in eine Zeichenfolge geändert wird, setzt das System die **IncludeInDebugDump** option `false`.  
  
 Wenn das System setzt die **IncludeInDebugDump** option `false`, dies möglicherweise vom Benutzer ausgewählten Wert außer Kraft gesetzt.  
  
 value  
 Der Wert einer benutzerdefinierten Variable kann ein Literal oder ein Ausdruck sein. Eine Variable enthält Optionen zum Festlegen des Variablenwerts und des Datentyps des Werts. Die beiden Eigenschaften müssen kompatibel sein. Beispielsweise ist das Verwenden eines string-Werts zusammen mit einem integer-Datentyp ungültig.  
  
 Falls die Variable so konfiguriert ist, dass sie als Ausdruck ausgewertet wird, müssen Sie einen Ausdruck angeben. Zur Laufzeit wird der Ausdruck ausgewertet, und die Variable wird auf das Auswertungsergebnis festgelegt. Wenn z. B. eine Variable den Ausdruck `DATEPART("month", GETDATE())` verwendet, entspricht der Wert der Variablen der Zahl des Monats im aktuellen Datum. Der Ausdruck muss ein gültiger Ausdruck sein, der die [!INCLUDE[ssIS](../includes/ssis-md.md)] -Ausdrucksgrammatiksyntax verwendet. Wenn ein Ausdruck mit Variablen verwendet wird, kann der Ausdruck Literale sowie die Operatoren und Funktionen der Ausdrucksgrammatik verwenden. Der Ausdruck kann jedoch nicht auf die Spalten in einem Datenfluss des Pakets verweisen. Die maximale Länge eines Ausdrucks beträgt 4000 Zeichen. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 ValueType  
 > [!NOTE]  
>  Der Eigenschaftswert wird in der Spalte **Datentyp** im Fenster **Variablen** angezeigt.  
  
 Gibt den Datentyp des Variablenwerts an.  
  
## <a name="configuring-variables"></a>Konfigurieren von Variablen  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)]-Designer festlegen können, finden Sie unter [Fenster „Variablen“](../../2014/integration-services/variables-window.md).  
  
 Weitere Informationen zu variableneigenschaften und Weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.Variable>.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
 [Festlegen der Eigenschaften von benutzerdefinierten Variablen](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)  
  
 [Verwenden der Werte von Variablen und Parametern in einem untergeordneten Paket](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [Zuordnen von Abfrageparametern zu Variablen in einer Datenflusskomponente](data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  