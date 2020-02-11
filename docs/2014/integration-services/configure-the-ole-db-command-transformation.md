---
title: Konfigurieren der Transformation für OLE DB Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [Integration Services]
- OLE DB Command transformation
ms.assetid: c800f167-3d2e-4c10-8ba3-a02f1872ccea
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8c9536e14f20e62b944df44ff943b05edb92e5fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060557"
---
# <a name="configure-the-ole-db-command-transformation"></a>Konfigurieren der Transformation für OLE DB-Befehl
  Das Paket muss bereits mindestens einen Datenflusstask und eine Quelle, wie z. B. eine Flatfilequelle oder eine OLE DB-Quelle, einschließen, damit Sie eine Transformation für OLE DB-Befehl hinzufügen und konfigurieren können. Diese Transformation wird normalerweise zum Ausführen parametrisierter Abfragen verwendet.  
  
### <a name="to-configure-the-ole-db-command-transformation"></a>So konfigurieren Sie die Transformation für OLE DB-Befehl  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Fenster **Toolbox**die Transformation für OLE DB-Befehl auf die Entwurfsoberfläche.  
  
4.  Verbinden Sie die Transformation für den OLE DB-Befehl mit dem Datenfluss, indem Sie einen Connector (der grüne oder rote Pfeil) von einer Datenquelle oder einer vorherigen Transformation mit der Maus auf die Transformation für den OLE DB-Befehl ziehen.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Komponente, und wählen Sie „Bearbeiten“ oder **Erweiterten Editor anzeigen**aus.  
  
6.  Wählen Sie auf der Registerkarte **Verbindungs-Manager** in der Liste **Verbindungs-Manager** einen OLE DB-Verbindungs-Manager aus. Weitere Informationen finden Sie unter [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).  
  
7.  Klicken Sie auf die Registerkarte **Komponenteneigenschaften**, und klicken Sie im Feld **SqlCommand** auf die Schaltfläche mit den Auslassungspunkten ( **...** ).  
  
8.  Geben Sie in **Zeichenfolgenwert-Editor**die parametrisierte SQL-Anweisung mithilfe eines Fragezeichens (?) als Parametermarkierung für jeden Parameter ein.  
  
9. Klicken Sie auf **Aktualisieren**. Wenn Sie auf **Aktualisieren**klicken, erstellt die Transformation eine Spalte für jeden Parameter in der Sammlung externer Spalten und legt die DBParamInfoFlags-Eigenschaft fest.  
  
10. Klicken Sie auf die Registerkarte **Eingabe- und Ausgabeeigenschaften** .  
  
11. Erweitern Sie **Eingabe des OLE DB-Befehls**und anschließend **Externe Spalten**.  
  
12. Überprüfen Sie, ob **Externe Spalten** eine Spalte für jeden Parameter in der SQL-Anweisung auflistet. Die Spaltennamen lauten **Param_0**, **Param_1**usw.  
  
     Die Spaltennamen sollten nicht geändert werden. Wenn Sie die Spaltennamen ändern, generiert [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] einen Überprüfungsfehler für die Transformation für den OLE DB-Befehl.  
  
     Der Datentyp sollte auch nicht geändert werden. Die DataType-Eigenschaft der einzelnen Spalten wird auf den entsprechenden Datentyp festgelegt.  
  
13. Falls **Externe Spalten** keine Spalten auflistet, müssen sie manuell hinzugefügt werden.  
  
    -   Klicken Sie für jeden Parameter in der SQL-Anweisung einmal auf **Spalte hinzufügen** .  
  
    -   Aktualisieren Sie die Spaltennamen auf **Param_0**, **Param_1**usw.  
  
    -   Geben Sie einen Wert in der DBParamInfoFlags-Eigenschaft an. Der Wert muss mit einem Wert in der OLE DB-Enumeration DBPARAMFLAGSENUM übereinstimmen. Weitere Informationen finden Sie in der OLE DB-Referenzdokumentation.  
  
    -   Geben Sie den Datentyp der Spalte und, in Abhängigkeit vom Datentyp, die Codepage, die Länge, die Genauigkeit und die Dezimalstellen der Spalte an.  
  
    -   Wenn Sie einen nicht verwendeten Parameter löschen möchten, wählen Sie den Parameter in **Externe Spalten**aus, und klicken Sie auf **Spalte entfernen**.  
  
    -   Klicken Sie auf **Spaltenzuordnungen** , und ordnen Sie Spalten in der Liste **Verfügbare Eingabespalten** Parametern in der Liste **Verfügbare Zielspalten** zu.  
  
14. Klicken Sie auf **OK**.  
  
15. Klicken Sie im Menü **Datei** auf **Speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transformation für OLE DB Befehl](data-flow/transformations/ole-db-command-transformation.md)   
 [SQL Server Integration Services-Transformationen](data-flow/transformations/integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](data-flow/integration-services-paths.md)   
 [Datenflusstask](control-flow/data-flow-task.md)  
  
  
