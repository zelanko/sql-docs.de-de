---
title: 'Aufgabe 14: Hinzufügen von Execute SQL Task zur Ablaufsteuerung, um die gespeicherte Prozedur für MDS auszuführen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: cf0a02e973d046f3dff2b2df95327cf38e88443c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027971"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a>Aufgabe 14: Hinzufügen von Execute SQL Task zur Ablaufsteuerung, um die gespeicherte Prozedur für MDS auszuführen
  Nachdem Sie Daten in die Stagingtabellen von MDS geladen haben, müssen Sie eine gespeicherte Prozedur ausführen, die der Tabelle zugeordnet ist, um die Daten aus dem Staging in die entsprechenden Tabellen in der MDS-Datenbank zu laden. Diese gespeicherte Prozedur hat zwei erforderliche Parameter, die Sie übergeben müssen: LogFlag und VersionName. LogFlag gibt an, ob Transaktionen während des Stagingprozesses protokolliert werden, und VersionName gibt die Version des Modells an. Finden Sie unter [gespeicherte Stagingprozedur](https://msdn.microsoft.com/library/hh231028.aspx) Weitere Informationen.  
  
 In dieser Aufgabe fügen Sie der Ablaufsteuerung den Task "SQL ausführen" hinzu, um die gespeicherte Prozedur aufzurufen und die bereitgestellten Daten in die entsprechenden MDS-Tabellen zu laden.  
  
1.  Wechseln Sie nun in der **Ablaufsteuerung** Registerkarte.  
  
2.  Drag & Drop **Execute SQL Task** aus der **SSIS-Toolbox** auf die **Ablaufsteuerung** Registerkarte.  
  
3.  Mit der rechten Maustaste **Execute SQL Task** in die **Ablaufsteuerung** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Trigger Stored Procedure to Load Data into MDS** , und drücken Sie **EINGABETASTE**.  
  
4.  Herstellen einer mit **Receive, Cleanse, Match und Curate Supplier Data** zu **Trigger Stored Procedure to Load Data** mithilfe des grünen Konnektors.  
  
     ![Herstellen einer Verbindung mit "SQL ausführen" ausführen](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "Herstellen einer Verbindung mit SQL-Task ausgeführt.")  
  
5.  Mithilfe der **Variablen** Fenster, fügen Sie zwei neue Variablen mit den folgenden Einstellungen hinzu. Wenn Sie nicht sehen die **Variablen** Fenster klicken Sie auf **SSIS** auf der Menüleiste und auf **Variablen**.  
  
    |Name|Datentyp|Wert|  
    |----------|---------------|-----------|  
    |LogFlag|Int32|1|  
    |VersionName|Zeichenfolge|VERSION_1|  
  
     ![SSIS-Variablen (Fenster)](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS-Variablen (Fenster)")  
  
6.  Doppelklicken Sie auf **Auslösen der gespeicherten Prozedur zum Laden von Daten in MDS**.  
  
7.  In der **Execute SQL Task Editor** wählen Sie im Dialogfeld **(lokal). MDS** (oder **"localhost". MDS**) für **Verbindung**.  
  
8.  Typ **EXEC [Stg]. [ Udp_Supplier_Leaf]?,?,?** für **SQL-Anweisung**. Sie können den Namen mit SQL Server Management Studio überprüfen.  
  
     ![Führen Sie SQL-Editor-Dialogfeld – Allgemeine Einstellungen](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "führen Sie SQL-Editor-Dialogfeld – Allgemeine Einstellungen")  
  
9. Klicken Sie auf **Parameterzuordnung** im Menü auf der linken Seite.  
  
10. In der **Parameterzuordnung** auf **hinzufügen** um eine Zuordnung hinzuzufügen. Maximieren Sie das Fenster, und passen Sie die Breite der Spalten so an, dass die Werte in den Dropdownlisten vollständig angezeigt werden.  
  
11. Wählen Sie **VersionName** aus der Dropdown-Liste für die **Variablenname**.  
  
12. Wählen Sie **NVARCHAR** für **Datentyp**.  
  
13. Typ **0** (null) **Parametername**.  
  
14. Wiederholen Sie die vorhergehenden vier Schritte, um zwei weitere Variablen hinzuzufügen.  
  
    |Variablenname|Datentyp (wichtig)|Parametername|  
    |-------------------|-----------------------------|--------------------|  
    |User::LogFlag|LONG|1|  
    |User::BatchTag|NVARCHAR|2|  
  
     ![Führen Sie SQL-Task-Editor – Parameterzuordnung](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "führen Sie SQL-Task-Editor – Parameterzuordnung")  
  
15. Klicken Sie auf **OK** schließen die **SQL-Editor ausführen** Dialogfeld.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 15: Erstellen und Ausführen des SSIS-Projekts](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)  
  
  
