---
title: 'Analysis Services Tutorial ergänzende Lektion: Dynamische Sicherheit | Microsoft-Dokumentation'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 9fbc474dbf7621b0da68edb7b310bb55ffcde7d5
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64776087"
---
# <a name="supplemental-lesson---dynamic-security"></a>Ergänzende Lektion: dynamische Sicherheit

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser ergänzenden Lektion erstellen Sie eine zusätzliche Rolle, die dynamische Sicherheit implementiert. Dynamische Sicherheit bietet Sicherheit auf Zeilenebene basierend auf dem Benutzernamen oder der Anmelde-ID des angemeldeten Benutzers. 
  
Um dynamische Sicherheit zu implementieren, fügen Sie eine Tabelle, für das Modell mit den Benutzernamen der Benutzer, die eine Verbindung mit dem Modell herstellen und Modellobjekte und Daten durchsuchen können. Das Modell, die Sie mithilfe dieses Tutorial ist im Kontext der Adventure Works; Um diese Lektion abschließen zu können, müssen Sie jedoch eine Tabelle mit Benutzern aus Ihrer eigenen Domäne hinzufügen. Sie benötigen nicht die Kennwörter für den Benutzernamen, die hinzugefügt werden. Um eine Tabelle "employeesecurity" mit einer kleinen Stichprobe von Benutzern aus Ihrer eigenen Domäne zu erstellen, verwenden Sie die Funktion zum Einfügen, Mitarbeiterdaten aus einem Excel-Arbeitsblatt. In einem realen Szenario wäre die Tabelle mit den Benutzernamen in der Regel eine Tabelle aus einer tatsächlichen Datenbank als Datenquelle; z. B. eine reale DimEmployee-Tabelle.  
  
Um dynamische Sicherheit zu implementieren, verwenden Sie zwei DAX-Funktionen: [USERNAME-Funktion (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f) und [LOOKUPVALUE-Funktion (DAX)](http://msdn.microsoft.com/73a51c4d-131c-4c33-a139-b1342d10caab). Diese Funktionen, die in einer Zeilenfilterformel angewendet werden, werden in einer neuen Rolle definiert. Mit der LOOKUPVALUE-Funktion, gibt die Formel einen Wert aus der Tabelle "employeesecurity" an. Die Formel übergibt Sie an, dass der Wert, der die USERNAME-Funktion, die den Namen des angemeldeten Benutzers angibt, die dieser Rolle gehört. Der Benutzer kann dann nur Daten, die vom Zeilenfilter der Rolle angegebenen durchsuchen. In diesem Fall geben Sie an, dass Verkaufsmitarbeiter nur internetumsatzdaten für die Vertriebsgebiete suchen können, in denen sie Mitglied sind.  
  
Aufgaben, die nur für dieses Adventure Works-Szenario für die Tabellenmodellierung relevant sind und nicht unbedingt in der realen Welt anwendbar sind, werden als solche identifiziert. Jede Aufgabe umfasst weitere Informationen, die den Zweck der Aufgabe beschreiben.  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **30 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

In diesem Artikel ergänzende Lektion ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser ergänzenden Lektion alle vorherigen Lektionen abgeschlossen haben.  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>Hinzufügen der dimSalesTerritory-Tabelle zum Projekt 'AW Internet Sales Tabular Model'  

Um dynamische Sicherheit für dieses Adventure Works-Szenario zu implementieren, müssen Sie dem Modell zwei weitere Tabellen hinzufügen. Die erste Tabelle, die Sie hinzufügen, ist die dimsalesterritory-Tabelle (als Vertriebsgebiet) aus der gleichen AdventureWorksDW-Datenbank. Später wenden Sie einen Zeilenfilter auf die Tabelle "salesterritory", die die betreffenden Daten definiert, die der angemeldete Benutzer durchsuchen kann.  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>So fügen Sie die Tabelle dimSalesTerritory hinzu  
  
1.  Im Tabellenmodell-Explorer > **Datenquellen**mit der rechten Maustaste auf die Verbindung, und klicken Sie dann auf **neue Tabelle importieren**.  

    Wenn der Identitätswechsel-Anmeldeinformationen im Dialogfeld angezeigt wird, geben Sie die Identitätswechselinformationen, die Sie in Lektion 2 verwendet: Hinzufügen von Daten.
  
2.  Wählen Sie im Navigator die **"dimsalesterritory"** Tabelle, und klicken Sie dann auf **OK**.    
  
3.  Im Abfrage-Editor, klicken Sie auf die **"dimsalesterritory"** abzufragen, und entfernen Sie **SalesTerritoryAlternateKey** Spalte.  
  
7.  Klicken Sie auf **Importieren**.  
  
    Die neue Tabelle wird am Ende des modellarbeitsbereichs hinzugefügt. Objekte und Daten aus der Quelltabelle "dimsalesterritory" werden dann in Ihre AW Internet Sales Tabular Model importiert.  
  
9. Nachdem die Tabelle erfolgreich importiert wurde, klicken Sie auf **schließen**.  

## <a name="add-a-table-with-user-name-data"></a>Hinzufügen einer Tabelle mit Benutzernamendaten  

Die Tabelle "dimemployee" in der Beispieldatenbank "AdventureWorksDW" enthält Benutzer aus der AdventureWorks-Domäne. Diese Benutzernamen sind nicht in Ihrer Umgebung vorhanden. Sie müssen eine Tabelle in Ihrem Modell erstellen, die einen kleinen Teil (mindestens drei) der tatsächlichen Benutzer in Ihrer Organisation enthält. Sie fügen dann diese Benutzer als Mitglieder der neuen Rolle. Sie benötigen nicht die Kennwörter für die beispielbenutzernamen, aber Sie benötigen tatsächliche Windows-Benutzernamen aus Ihrer eigenen Domäne.  
  
#### <a name="to-add-an-employeesecurity-table"></a>Hinzufügen eine Tabelle "employeesecurity"  
  
1.  Öffnen Sie Microsoft Excel, erstellen Sie ein Arbeitsblatt.  
  
2.  Kopieren Sie die folgende Tabelle, einschließlich der Kopfzeile, und fügen Sie sie dann in das Arbeitsblatt ein.  

    ```
      |EmployeeId|SalesTerritoryId|FirstName|LastName|LoginId|  
      |---------------|----------------------|--------------|-------------|------------|  
      |1|2|<user first name>|<user last name>|\<domain\username>|  
      |1|3|<user first name>|<user last name>|\<domain\username>|  
      |2|4|<user first name>|<user last name>|\<domain\username>|  
      |3|5|<user first name>|<user last name>|\<domain\username>|  
    ```

3.  Ersetzen Sie den Vornamen, Nachnamen und "Domäne\Benutzername" mit den Namen und Anmelde-Ids von drei Benutzern in Ihrer Organisation an. Geben Sie den gleichen Benutzer in den ersten beiden Zeilen für EmployeeId 1, angezeigt, dass dieser Benutzer mehr als einem Vertriebsgebiet angehört. Lassen Sie die Felder "EmployeeID" und "salesterritoryid" aus, wie sie sind.  
  
4.  Speichern Sie das Arbeitsblatt als **"sampleemployee"**.  
  
5.  Wählen Sie im Arbeitsblatt alle Zellen mit Mitarbeiterdaten, einschließlich des Headers, und klicken Sie dann mit der rechten Maustaste in der ausgewählten Daten, und klicken Sie dann auf **Kopie**.  
  
6.  Klicken Sie in SSDT auf das **bearbeiten** , und klicken Sie dann auf **einfügen**.  
  
    Wenn einfügen abgeblendet ist, klicken Sie auf eine Spalte in eine beliebige Tabelle im Modell-Designer-Fenster, und versuchen Sie es erneut.  
  
7.  In der **Vorschau einfügen** Dialogfeld **Tabellenname**, Typ **"employeesecurity"**.  
  
8.  In **einzufügende Daten**, ob die Daten alle Benutzerdaten und Kopfzeilen aus dem Arbeitsblatt "sampleemployee" einschließen.  
  
9. Überprüfen Sie, ob **Erste Zeile als Spaltenüberschriften verwenden** aktiviert ist, und klicken Sie anschließend auf **OK**.  
  
    Es wird eine neue Tabelle mit dem Namen "employeesecurity" mit aus dem Arbeitsblatt "sampleemployee" kopierten Angestelltendaten erstellt.  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>Erstellen von Beziehungen zwischen Tabellen "factinternetsales", DimGeography, und "dimsalesterritory"  

In der Tabelle "factinternetsales" DimGeography und "dimsalesterritory" enthält jeweils die Spalte "salesterritoryid". Die Spalte "salesterritoryid" in der Tabelle "dimsalesterritory" enthält die Werte mit einer anderen Id für jedes Vertriebsgebiet.  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>So erstellen Sie Beziehungen zwischen der "factinternetsales", DimGeography und die Tabelle "dimsalesterritory"  
  
1.  In der Diagrammsicht in der **DimGeography** Tabellen, warten Sie, und klicken Sie auf die **"salesterritoryid"** Spalte ziehen Sie dann den Cursor zu der **"salesterritoryid"** -Spalte in der **"Dimsalesterritory"** Tabelle, und veröffentlichen.  
  
2.  In der **"factinternetsales"** Tabellen, warten Sie, und klicken Sie auf der **"salesterritoryid"** Spalte ziehen Sie dann den Cursor zu der **"salesterritoryid"** -Spalte in der  **"Dimsalesterritory"** Tabelle, und veröffentlichen.  
  
    Beachten Sie, dass die Eigenschaft aktiv für diese Beziehung ist "false", was bedeutet, dass sie aktiv ist. Die Tabelle "factinternetsales" verfügt bereits über eine andere aktive Beziehung.  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>Ausblenden der Tabelle "employeesecurity" aus Client-Anwendungen  

In dieser Aufgabe blenden Sie die Tabelle "employeesecurity", sodass sie in der Feldliste einer Clientanwendung angezeigt werden. Bedenken Sie, die eine Tabelle durch die Ausblendung nicht geschützt wird. Benutzer können trotzdem Tabellendaten "employeesecurity" Abfragen, wenn sie wissen, wie. Um die Daten der "employeesecurity", Benutzer daran hindern, werden alle Daten, Abfragen zu schützen. Wenden Sie einen Filter in einer späteren Aufgabe.  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>So blenden Sie die Tabelle "employeesecurity" aus Client-Anwendungen aus  
  
-   Klicken Sie im Modell-Designer in der Diagrammsicht mit der rechten Maustaste auf die Tabellenkopfzeile **Employee** (Angestellter), und klicken Sie anschließend auf **Aus Clienttools ausblenden**.  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Erstellen der Benutzerrolle 'Sales Employees by Territory'  

In dieser Aufgabe erstellen Sie eine Benutzerrolle an. Diese Rolle umfasst einen Zeilenfilter definieren, welche Zeilen der Tabelle "dimsalesterritory" für Benutzer sichtbar sind. Der Filter wird dann in die Richtung der 1: n Beziehung auf alle anderen Tabellen, die im Zusammenhang mit "dimsalesterritory" angewendet. Außerdem wenden Sie einen Filter, der sichert die gesamte Tabelle "employeesecurity", wird von jedem Benutzer, der ein Mitglied der Rolle ist.  
  
> [!NOTE]  
> Die Rolle Sales Employees by Territory, die Sie in dieser Lektion erstellen, schränkt Mitglieder ein, sodass sie nur Umsatzdaten für das Vertriebsgebiet suchen (oder abfragen) können, zu dem sie gehören. Wenn Sie einen Benutzer als Mitglied für die Sales-Mitarbeiter nach Territory-Rolle, die auch vorhanden ist hinzufügen, wie ein Element in einer Rolle in erstellt [Lektion 11: Erstellen von Rollen](../tutorial-tabular-1400/as-lesson-11-create-roles.md), erhalten Sie eine Kombination von Berechtigungen. Wenn ein Benutzer Mitglied mehrerer Rollen ist, sind die für jede Rolle definierten Berechtigungen und Zeilenfilter kumulativ. Das heißt, hat der Benutzer durch die Kombination von Rollen höhere Berechtigungen.  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>So erstellen Sie die Benutzerrolle 'Sales Employees by Territory'  
  
1.  Klicken Sie in SSDT auf das **Modell** , und klicken Sie dann auf **Rollen**.  
  
2.  In **Rollen-Manager**, klicken Sie auf **neu**.  
  
    Der Liste wird eine neue Rolle mit der Berechtigung Keine hinzugefügt.  
  
3.  Klicken Sie auf die neue Rolle, und klicken Sie dann in der **Namen** Spalte benennen Sie die Rolle in **Sales Employees by Territory**.  
  
4.  Klicken Sie in der Spalte **Berechtigungen** auf die Dropdownliste, und wählen Sie anschließend die Berechtigung **Lesen** aus.  
  
5.  Klicken Sie auf die **Mitglieder** Registerkarte, und klicken Sie dann auf **hinzufügen**.  
  
6.  In der **Benutzer oder Gruppe auswählen** Dialogfeld **Geben Sie die zu verwendenden Objektnamen auswählen**, geben Sie den ersten beispielbenutzernamen ein, den Sie beim Erstellen der Tabelle "employeesecurity" verwendet. Klicken Sie auf **Namen überprüfen** , um die Gültigkeit des Benutzernamens zu überprüfen, und klicken Sie anschließend auf **OK**.  
  
    Wiederholen Sie diesen Schritt, und fügen die anderen beispielbenutzernamen, die Sie beim Erstellen der Tabelle "employeesecurity" verwendet.  
  
7.  Klicken Sie auf die **Zeilenfilter** Registerkarte.  
  
8.  Für die **"employeesecurity"** -Tabelle in der **DAX-Filter** Spalte Geben Sie die folgende Formel:  
  
    ```
      =FALSE()  
    ```
  
    Diese Formel gibt an, dass alle Spalten in der falschen booleschen Bedingung aufgelöst. Keine Spalten für die Tabelle "employeesecurity" können von einem Mitglied der Sales Employees von der Benutzerrolle "Territory" abgefragt werden.  
  
9. Für die **"dimsalesterritory"** Tabelle, und geben Sie die folgende Formel:  

    ```  
    ='DimSalesTerritory'[SalesTerritoryKey]=LOOKUPVALUE('EmployeeSecurity'[SalesTerritoryId], 
      'EmployeeSecurity'[LoginId], USERNAME(), 
      'EmployeeSecurity'[SalesTerritoryId], 'DimSalesTerritory'[SalesTerritoryKey]) 
    ```
  
    In dieser Formel gibt die LOOKUPVALUE-Funktion alle Werte für die DimEmployeeSecurity [SalesTerritoryId]-Spalte, wobei der "employeesecurity [LoginId]" ist identisch mit dem aktuell angemeldeten Windows-Benutzernamen und "employeesecurity [SalesTerritoryId]" zurück, mit die identisch mit "mit" DimSalesTerritory [SalesTerritoryId].  
  
    Der Satz von IDs von LOOKUPVALUE zurückgegebenen Vertriebsgebiet wird dann verwendet, um die in der Tabelle "dimsalesterritory" gezeigten Zeilen einzuschränken. Nur Zeilen, in denen "salesterritoryid" für die Zeile im Satz von IDs, die von der LOOKUPVALUE-Funktion zurückgegeben wird, werden angezeigt.  
  
10. Klicken Sie im Rollen-Manager **Ok**.  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Testen der Benutzerrolle 'Sales Employees by Territory'  

In dieser Aufgabe verwenden Sie die analysieren in Excel-Funktion in SSDT um die Wirksamkeit der Sales Employees von Rolle "Benutzer" Territory zu testen. Sie geben Sie einen der Benutzernamen an, die Sie in der Tabelle "employeesecurity" und als Mitglied der Rolle hinzugefügt haben. Dieser Benutzername wird dann als der effektive Benutzername in der Verbindung zwischen Excel und das Modell verwendet.  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>So testen Sie die Benutzerrolle 'Sales Employees by Territory'  
  
1.  Klicken Sie in SSDT auf das **Modell** , und klicken Sie dann auf **in Excel analysieren**.  
  
2.  Wählen Sie im Dialogfeld **In Excel analysieren** in **Geben Sie den Benutzernamen oder die Rolle für die Verbindung mit dem Modell an**die Option **Anderer Windows-Benutzer**aus, und klicken Sie anschließend auf **Durchsuchen**.  
  
3.  In der **Benutzer oder Gruppe auswählen** Dialogfeld **Geben Sie den zu verwendenden Objektnamen**, geben Sie einen Benutzernamen ein, die Sie in der Tabelle "employeesecurity" einbezogen haben, und klicken Sie dann auf **Namen überprüfen**.  
  
4.  Klicken Sie auf **OK** , um das Dialogfeld **Benutzer oder Gruppe auswählen** zu schließen. Klicken Sie anschließend auf **OK** , um das Dialogfenster **In Excel analysieren** zu schließen.  
  
    Excel wird mit einer neuen Arbeitsmappe geöffnet. Eine PivotTable wird automatisch erstellt. Die Liste PivotTable Fields enthält die meisten Datenfelder, im neuen Modell verfügbar sind.  
  
    Beachten Sie, dass die Tabelle "employeesecurity" ist nicht in der PivotTable-Fields-Liste angezeigt. Sie ausgeblendet haben diese Tabelle aus den Clienttools in der vorherigen Aufgabe.  
  
5.  In der **Felder** aufzulisten, im **∑ Internet Sales** (Measures), wählen Sie die **"internettotalsales" an** Measure. Das Measure in eingegeben wird die **Werte** Felder.  
  
6.  Wählen Sie die **"salesterritoryid"** Spalte aus der **"dimsalesterritory"** Tabelle. In die Spalte eingegeben wird die **Zeilenbezeichnungen** Felder.  
  
    Die Internetumsatzzahlen werden nur für den einen Bereich angezeigt, dem der gültige Benutzername, den Sie verwendet haben, zugeordnet haben. Wenn Sie eine andere Spalte, z. B. City, aus der Tabelle "DimGeography" als zeilenbeschriftungsfeld, auswählen, werden nur Orte im Vertriebsgebiet, zu dem der effektive Benutzer angehört, angezeigt.  
    Dieser Benutzer nicht durchsuchen oder Abfragen alle Internet-Umsatzdaten für Vertriebsgebiete als die, denen sie angehören. Diese Einschränkung wird der Zeilenfilter definiert, für die Tabelle "dimsalesterritory" in der Sales Employees by Territory-Benutzerrolle Daten für alle Daten, die im Zusammenhang mit anderen verkaufsgebieten schützt.  
  
## <a name="see-also"></a>Siehe auch  

[USERNAME-Funktion (DAX)](https://msdn.microsoft.com/library/hh230954.aspx)  
[LOOKUPVALUE-Funktion (DAX)](https://msdn.microsoft.com/library/gg492170.aspx)  
[CUSTOMDATA-Funktion (DAX)](https://msdn.microsoft.com/library/hh213140.aspx)  
