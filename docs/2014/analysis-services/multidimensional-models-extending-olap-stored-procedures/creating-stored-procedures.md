---
title: Erstellen gespeicherter Prozeduren | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62703090"
---
# <a name="creating-stored-procedures"></a>Erstellen gespeicherter Prozeduren
  Alle gespeicherten Prozeduren müssen mit einer CLR-Klasse (Common Language Runtime) oder einer COM-Klasse (Component Object Model) verknüpft sein, damit sie verwendet werden können. Die-Klasse muss auf dem Server installiert sein (in der Regel in Form [!INCLUDE[msCoName](../../includes/msconame-md.md)] eines ActiveX-® Dynamic Link Library (dll)) und als Assembly auf dem Server oder in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank registriert.  
  
 Gespeicherte Prozeduren sind auf einem Server oder in einer Datenbank registriert. Gespeicherte Serverprozeduren können aus einem beliebigen Abfragekontext aufgerufen werden. Der Zugriff auf gespeicherte Datenbankprozeduren ist nur möglich, wenn der Datenbankkontext die Datenbank ist, unter der die gespeicherte Prozedur definiert ist. Wenn Funktionen in einer Assembly die Funktionen in einer anderen Assembly aufrufen, müssen Sie beide Assemblys in demselben Kontext registrieren (Server oder Datenbank). Für einen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Server oder eine bereitgestellte Datenbank auf einem-Server können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, um eine Assembly zu registrieren. Für ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekt können Sie eine Assembly mithilfe von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Designer im Projekt registrieren.  
  
> [!IMPORTANT]  
>  COM-Assemblys können ein Sicherheitsrisiko darstellen. Aufgrund dieses Risikos und anderer Überlegungen wurden COM-Assemblys in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]als veraltet markiert. COM-Assemblys werden in zukünftigen Versionen möglicherweise nicht mehr unterstützt.  
  
## <a name="registering-a-server-assembly"></a>Registrieren einer Serverassembly  
 Im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] werden Serverassemblys im Ordner Assemblys unter einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aufgelistet. Serverassemblys können sowohl .NET-Assemblys (CLR) als auch COM-Bibliotheken enthalten.  
  
### <a name="to-create-a-server-assembly"></a>So erstellen Sie eine Serverassembly  
  
1.  Erweitern Sie in Objekt-Explorer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Instanz von, klicken Sie mit **der rechten** Maustaste auf den Ordner Assemblys, und klicken Sie auf **neue Assembly**. Dadurch wird das Dialogfeld **Serverassembly registrieren** angezeigt.  
  
2.  Geben Sie für **Typ** den Typ der Assembly an:  
  
    -   Für eine DLL mit verwaltetem Code (CLR) geben Sie .NET-Assembly an.  
  
    -   Geben Sie für eine com-dll (Native Code) com dll an.  
  
3.  Geben Sie unter **Dateiname**die dll an, die die gespeicherten Prozeduren enthält.  
  
4.  Geben **** Sie unter AssemblyName einen Namen für die Assembly an.  
  
5.  Wenn es sich um einen Debugbuild der Bibliothek handelt, die Sie zum Debuggen gespeicherter Prozeduren verwenden möchten, aktivieren Sie das Kontrollkästchen **Debuginformationen einschließen** . Weitere Informationen zum Debuggen gespeicherter Prozeduren finden Sie unter [Debuggen von gespeicherten](debugging-stored-procedures.md)  
  
6.  Sie können auf **OK** klicken, um die Assembly sofort zu registrieren, oder Sie können auf der Symbolleiste des Dialog Felds auf einen Befehl im Menü **Skript** klicken, um ein Skript für die Registrierungsaktion in ein Abfragefenster, eine Datei oder die Zwischenablage zu schreiben.  
  
 Nachdem Sie eine Serverassembly registriert haben, können Sie Sie konfigurieren, indem Sie in Objekt-Explorer mit der rechten Maustaste auf die Assembly und dann auf **Eigenschaften**klicken.  
  
## <a name="registering-a-database-assembly-on-the-server"></a>Registrieren einer Datenbankassembly auf dem Server  
 Im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] werden Datenbankassemblys im Ordner Assemblys unter einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank aufgelistet. Datenbankassemblys können sowohl .NET-Assemblys (CLR) als auch COM-Bibliotheken enthalten.  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>So erstellen Sie eine Datenbankassembly auf einem Server  
  
1.  Erweitern Sie die Instanz [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] der Datenbank Objekt-Explorer, klicken Sie mit der rechten Maustaste auf **den Ordner** Assemblys, und klicken Sie dann auf **neue Assembly**. Dadurch wird das Dialogfeld **Datenbankassembly registrieren** angezeigt.  
  
2.  Geben Sie für **Typ** den Typ der Assembly an:  
  
    -   Für eine DLL mit verwaltetem Code (CLR) geben Sie .NET-Assembly an.  
  
    -   Für eine DLL mit systemeigenem Code (COM) geben Sie COM-DLL an.  
  
3.  Geben Sie unter **Dateiname**die dll an, die die gespeicherten Prozeduren enthält.  
  
4.  Geben **** Sie unter AssemblyName einen Namen für die Assembly an.  
  
5.  Wenn es sich um einen Debugbuild der Bibliothek handelt, die Sie zum Debuggen gespeicherter Prozeduren verwenden möchten, aktivieren Sie das Kontrollkästchen **Debuginformationen einschließen** . Weitere Informationen zum Debuggen gespeicherter Prozeduren finden Sie unter [Debuggen von gespeicherten](debugging-stored-procedures.md)  
  
6.  Sie können auf **OK** klicken, um die Assembly sofort zu registrieren, oder Sie können auf der Symbolleiste des Dialog Felds auf einen Befehl im Menü **Skript** klicken, um ein Skript für die Registrierungsaktion in ein Abfragefenster, eine Datei oder die Zwischenablage zu schreiben.  
  
 Nachdem Sie eine Datenbankassembly registriert haben, können Sie Sie konfigurieren, indem Sie in Objekt-Explorer mit der rechten Maustaste auf die Assembly und dann auf **Eigenschaften**klicken.  
  
## <a name="registering-a-database-assembly-in-a-project"></a>Registrieren einer Datenbankassembly in einem Projekt  
 Im Projektmappen-Explorer von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] werden Datenbankassemblys im Ordner Assemblys unter einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekt aufgelistet. Datenbankassemblys können sowohl .NET-Assemblys (CLR) als auch COM-Bibliotheken enthalten.  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>So erstellen Sie eine Datenbankassembly in einem Analysis Services-Projekt  
  
1.  Erweitern Sie die Instanz [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] der Datenbank in Objekt-Explorer, klicken Sie mit **der rechten** Maustaste auf den Ordner Assemblys, und klicken Sie dann auf **New Assembly Reference** Dadurch wird das Dialogfeld **Verweis hinzufügen** angezeigt. Auf der Registerkarte **.net** des Dialog Felds **Verweis hinzufügen** werden vorhandene .NET-Assemblys (CLR) aufgelistet, während auf der Registerkarte **Projekte** Projekte aufgeführt sind.  
  
2.  Sie können auf eine vorhandene Komponente oder ein vorhandenes Projekt klicken und dann auf **Hinzufügen** klicken, um Sie dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt hinzuzufügen. Um einen Verweis auf eine COM-DLL hinzuzufügen, klicken Sie auf die Registerkarte **Durchsuchen** , um die Datei zu suchen In der Liste **Ausgewählte Projekte und Komponenten** werden Name, Typ, Version und Speicherort für jede Komponente angezeigt, die Sie dem Projekt hinzufügen.  
  
3.  Wenn Sie die hinzu zufügenden Komponenten ausgewählt haben, klicken Sie auf **OK** , [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] um Sie dem Projekt hinzuzufügen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von mehrdimensionalen Modellen](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definieren von gespeicherten Prozeduren](defining-stored-procedures.md)  
  
  
