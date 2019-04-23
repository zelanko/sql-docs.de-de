---
title: Erstellen von gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7beb77adf595b055a6c1e4a7543b428a06ce7640
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158546"
---
# <a name="creating-stored-procedures"></a>Erstellen gespeicherter Prozeduren
  Alle gespeicherten Prozeduren müssen mit einer CLR-Klasse (Common Language Runtime) oder einer COM-Klasse (Component Object Model) verknüpft sein, damit sie verwendet werden können. Die Klasse muss installiert sein, auf dem Server – in der Regel in Form einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Dynamic link Library (DLL) - und registriert als Assembly auf dem Server oder in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank.  
  
 Gespeicherte Prozeduren sind auf einem Server oder in einer Datenbank registriert. Gespeicherte Serverprozeduren können aus einem beliebigen Abfragekontext aufgerufen werden. Der Zugriff auf gespeicherte Datenbankprozeduren ist nur möglich, wenn der Datenbankkontext die Datenbank ist, unter der die gespeicherte Prozedur definiert ist. Wenn Funktionen in einer Assembly die Funktionen in einer anderen Assembly aufrufen, müssen Sie beide Assemblys in demselben Kontext registrieren (Server oder Datenbank). Für einen Server oder eine bereitgestellte [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank auf einem Server können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zum Registrieren einer Assembly. Für ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekt können Sie eine Assembly mithilfe von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Designer im Projekt registrieren.  
  
> [!IMPORTANT]  
>  COM-Assemblys können ein Sicherheitsrisiko darstellen. Aufgrund dieses Risikos und anderer Überlegungen wurden COM-Assemblys in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]als veraltet markiert. COM-Assemblys werden in zukünftigen Versionen möglicherweise nicht mehr unterstützt.  
  
## <a name="registering-a-server-assembly"></a>Registrieren einer Serverassembly  
 Im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] werden Serverassemblys im Ordner Assemblys unter einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aufgelistet. Serverassemblys können sowohl .NET-Assemblys (CLR) als auch COM-Bibliotheken enthalten.  
  
### <a name="to-create-a-server-assembly"></a>So erstellen Sie eine Serverassembly  
  
1.  Erweitern Sie die Instanz [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im Objekt-Explorer mit der Maustaste der **Assemblys** Ordner, und klicken Sie dann auf **neue Assembly**. Dies zeigt die **Serverassembly** Dialogfeld.  
  
2.  Für **Typ** Geben Sie den Typ der Assembly:  
  
    -   Für eine DLL mit verwaltetem Code (CLR) geben Sie .NET-Assembly an.  
  
    -   Geben Sie für einen nativen Code (COM-DLL) COM-DLL.  
  
3.  Für **Dateiname**, geben Sie die DLL, die die gespeicherten Prozeduren enthält.  
  
4.  Für **Assemblyname**, geben Sie einen Namen für die Assembly.  
  
5.  Wenn ein Debugbuild der Bibliothek, dass Sie beabsichtigen, die zum Debuggen verwenden gespeicherte Prozeduren, wählen Sie die **Debuginformationen einschließen** Kontrollkästchen. Weitere Informationen zum Debuggen von gespeicherter Prozeduren finden Sie unter [gespeicherte Prozeduren Debuggen](debugging-stored-procedures.md).  
  
6.  Klicken Sie auf **OK** zum Registrieren der Assemblys sofort, oder klicken Sie auf der Symbolleiste des Dialogfelds können Sie einen Befehl klicken, auf die **Skript** Menü, um das Skript für der Registrierungsaktion ein Abfragefenster, einer Datei oder die Zwischenablage.  
  
 Nachdem Sie eine Serverassembly registrieren, können Sie diese konfigurieren, indem Sie mit der rechten Maustaste in der Assembly im Objekt-Explorer, und klicken Sie dann auf **Eigenschaften**.  
  
## <a name="registering-a-database-assembly-on-the-server"></a>Registrieren einer Datenbankassembly auf dem Server  
 Im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] werden Datenbankassemblys im Ordner Assemblys unter einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank aufgelistet. Datenbankassemblys können sowohl .NET-Assemblys (CLR) als auch COM-Bibliotheken enthalten.  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>So erstellen Sie eine Datenbankassembly auf einem Server  
  
1.  Erweitern Sie die Instanz der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank im Objekt-Explorer, mit der rechten Maustaste die **Assemblys** Ordner, und klicken Sie dann auf **neue Assembly**. Dies zeigt die **Datenbankassembly** Dialogfeld.  
  
2.  Für **Typ** Geben Sie den Typ der Assembly:  
  
    -   Für eine DLL mit verwaltetem Code (CLR) geben Sie .NET-Assembly an.  
  
    -   Für eine DLL mit systemeigenem Code (COM) geben Sie COM-DLL an.  
  
3.  Für **Dateiname**, geben Sie die DLL, die die gespeicherten Prozeduren enthält.  
  
4.  Für **Assemblyname**, geben Sie einen Namen für die Assembly.  
  
5.  Wenn ein Debugbuild der Bibliothek, dass Sie beabsichtigen, die zum Debuggen verwenden gespeicherte Prozeduren, wählen Sie die **Debuginformationen einschließen** Kontrollkästchen. Weitere Informationen zum Debuggen von gespeicherter Prozeduren finden Sie unter [gespeicherte Prozeduren Debuggen](debugging-stored-procedures.md).  
  
6.  Klicken Sie auf **OK** zum Registrieren der Assemblys sofort, oder klicken Sie auf der Symbolleiste des Dialogfelds können Sie einen Befehl klicken, auf die **Skript** Menü, um das Skript für der Registrierungsaktion ein Abfragefenster, einer Datei oder die Zwischenablage.  
  
 Nachdem Sie eine Datenbankassembly registrieren, können Sie diese konfigurieren, indem Sie mit der rechten Maustaste in der Assembly im Objekt-Explorer, und klicken Sie dann auf **Eigenschaften**.  
  
## <a name="registering-a-database-assembly-in-a-project"></a>Registrieren einer Datenbankassembly in einem Projekt  
 Im Projektmappen-Explorer von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] werden Datenbankassemblys im Ordner Assemblys unter einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekt aufgelistet. Datenbankassemblys können sowohl .NET-Assemblys (CLR) als auch COM-Bibliotheken enthalten.  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>So erstellen Sie eine Datenbankassembly in einem Analysis Services-Projekt  
  
1.  Erweitern Sie die Instanz der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank im Objekt-Explorer, mit der rechten Maustaste die **Assemblys** Ordner, und klicken Sie dann auf **neuer Assemblyverweis**. Dies zeigt die **Verweis hinzufügen** Dialogfeld. Die **.NET** Registerkarte die **Verweis hinzufügen** Dialogfeld Listet vorhandene Assemblys für .NET (CLR), während die **Projekte** Registerkarte werden die Projekte aufgelistet.  
  
2.  Sie können klicken Sie auf eine vorhandene Komponente oder ein Projekt, und klicken Sie dann auf **hinzufügen** zum Hinzufügen der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt. Um einen Verweis auf eine COM-DLL hinzuzufügen, klicken Sie auf die **Durchsuchen** Tab, um die Datei nicht finden. Die **ausgewählte Projekte und Komponenten** Liste zeigt die Namen, Typ, Version und Speicherort für jede Komponente, die Sie dem Projekt hinzufügen.  
  
3.  Wenn Sie nach Auswahl der Komponenten hinzuzufügen, klicken Sie auf **OK** zum Hinzufügen der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt.  
  
## <a name="script-format-for-an-assembly"></a>Skriptformat für eine Assembly  
 Das Registrieren einer .NET-Assembly ist ein relativ einfacher Vorgang. Eine .NET-Assembly wird im Binärformat einer Datenbank mithilfe des folgenden Formats hinzugefügt:  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von mehrdimensionalen Modellassemblys](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definieren gespeicherter Prozeduren](defining-stored-procedures.md)  
  
  
