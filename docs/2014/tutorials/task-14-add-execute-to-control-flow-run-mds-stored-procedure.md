---
title: 'Aufgabe 14: Hinzufügen von Execute SQL Task zur Ablauf Steuerung, um die gespeicherte Prozedur für MDS auszuführen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3fe1eb6032d9d550b36252e16eee51c98c5d2384
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65477102"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a>Aufgabe 14: Hinzufügen von Execute SQL Task zur Ablaufsteuerung, um die gespeicherte Prozedur für MDS auszuführen
  Nachdem Sie Daten in die Stagingtabellen von MDS geladen haben, müssen Sie eine gespeicherte Prozedur ausführen, die der Tabelle zugeordnet ist, um die Daten aus dem Staging in die entsprechenden Tabellen in der MDS-Datenbank zu laden. Diese gespeicherte Prozedur hat zwei erforderliche Parameter, die Sie übergeben müssen: LogFlag und VersionName. LogFlag gibt an, ob Transaktionen während des Stagingprozesses protokolliert werden, und VersionName gibt die Version des Modells an. Weitere Informationen finden Sie im Thema [gestaffelte gespeicherte Prozeduren](https://msdn.microsoft.com/library/hh231028.aspx) .  
  
 In dieser Aufgabe fügen Sie der Ablaufsteuerung den Task "SQL ausführen" hinzu, um die gespeicherte Prozedur aufzurufen und die bereitgestellten Daten in die entsprechenden MDS-Tabellen zu laden.  
  
1.  Wechseln Sie nun zur Registerkarte **Ablauf Steuerung** .  
  
2.  Ziehen Sie den **Task SQL ausführen** aus der **SSIS-Toolbox** auf die Registerkarte **Ablauf Steuerung** .  
  
3.  Klicken Sie in der Registerkarte **Ablauf Steuerung** mit der rechten Maustaste auf **SQL ausführen** , und klicken Sie auf **Umbenennen**. Geben Sie **die gespeicherte Prozedur zum Laden von Daten in MDS ein,** und drücken **Sie Eingabe**Taste.  
  
4.  Verbinden von **Empfangs-, Bereinigung-, überein** stimmenden und angleichen Lieferantendaten, um die **gespeicherte Prozedur zum Laden von Daten** mithilfe des grünen Connectors zu veranlassen.  
  
     ![Verbinden mit dem Task "SQL ausführen"](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "Verbinden mit dem Task "SQL ausführen"")  
  
5.  Fügen Sie mithilfe des Fensters **Variablen** zwei neue Variablen mit den folgenden Einstellungen hinzu. Wenn das Fenster **Variablen** nicht angezeigt wird, klicken Sie in der Menüleiste auf **SSIS** , und klicken Sie dann auf **Variablen**.  
  
    |Name|Datentyp|value|  
    |----------|---------------|-----------|  
    |LogFlag|Int32|1|  
    |VersionName|String|VERSION_1|  
  
     ![SSIS-Variablen (Fenster)](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS-Variablen (Fenster)")  
  
6.  Doppelklicken Sie **auf gespeicherte Prozedur ausführen, um Daten in MDS zu laden**.  
  
7.  Wählen Sie im Dialogfeld Editor für den **Task ' SQL ausführen** ' **(lokal) aus. MDS** (oder **localhost. MDS**) für die **Verbindung**.  
  
8.  Geben Sie **EXEC [STG]. [ein. udp_Supplier_Leaf]?,?,?** für die **SQL-Anweisung**. Sie können den Namen mit SQL Server Management Studio überprüfen.  
  
     ![Editor für den Task "SQL ausführen" (Dialogfeld) – Allgemeine Einstellungen](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "Editor für den Task "SQL ausführen" (Dialogfeld) – Allgemeine Einstellungen")  
  
9. Klicken Sie im Menü auf der linken Seite auf **Parameter Zuordnung** .  
  
10. Klicken Sie auf der Seite **Parameter Zuordnung** auf **Hinzufügen** , um eine Zuordnung hinzuzufügen. Maximieren Sie das Fenster, und passen Sie die Breite der Spalten so an, dass die Werte in den Dropdownlisten vollständig angezeigt werden.  
  
11. Wählen Sie **User:: VersionName** aus der Dropdown Liste für den **Variablennamen**aus.  
  
12. Wählen Sie **nvarchar** als **Datentyp**aus.  
  
13. Geben Sie **0** (null) für den **Parameter Namen**ein.  
  
14. Wiederholen Sie die vorhergehenden vier Schritte, um zwei weitere Variablen hinzuzufügen.  
  
    |Variablenname|Datentyp (wichtig)|Parametername|  
    |-------------------|-----------------------------|--------------------|  
    |User::LogFlag|LONG|1|  
    |User::BatchTag|NVARCHAR|2|  
  
     ![Editor für den Task "SQL ausführen" – Parameterzuordnung](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "Editor für den Task "SQL ausführen" – Parameterzuordnung")  
  
15. Klicken Sie auf **OK** , um das Dialogfeld **SQL-Editor ausführen** zu schließen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 15: Erstellen und Ausführen des SSIS-Projekts](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)  
  
  
