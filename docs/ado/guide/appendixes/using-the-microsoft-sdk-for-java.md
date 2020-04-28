---
title: Verwenden des Microsoft SDK für Java | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Java (Microsoft SDK for)
- Microsoft SDK for Java [ADO]
ms.assetid: 2d7cb5b5-8307-49dd-b07e-c07069bb1626
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0e6c5f2eb5ad792141e77122ff9e132d97f62ae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926467"
---
# <a name="using-the-microsoft-sdk-for-java"></a>Verwenden des Microsoft SDK für Java

> [!IMPORTANT]
> Microsoft hat den Support von Visual J++ im Januar 2004 nicht mehr unterstützt.

Das Microsoft SDK für Java ist das Developer Kit für die Microsoft Internet Explorer-Umgebung. Es werden Tools, Informationen und Beispiele bereitgestellt, die Sie bei der Entwicklung von Java-Programmen und-Applets basierend auf JDK 1,1 und dem virtuellen Microsoft-Win32-Computer (Microsoft VM) unterstützen. Das Microsoft SDK für Java ist nicht an Microsoft Visual J++ gebunden. Klicken Sie hier, um dieses SDK herunterzuladen.  
  
 Das Hilfsprogramm "JActiveX. exe" generiert Klassen aus einer Typbibliothek, kann aber nur in der Befehlszeile aufgerufen werden. Diese Funktion ist nicht in die Visual J++-Entwicklungsumgebung integriert. Im Unterschied zu den vom Assistenten für die Java-Typbibliothek generierten Klassen können Sie die vom SDK erstellten Klassen Wrapper schrittweise durchlaufen. Dies ist nützlich für das Debuggen, wie der Code die ADO-Wrapper Klassen verwendet.  
  
 Dieser Mechanismus liest die ADO-Typbibliothek und generiert Klassen, die Sie in Ihrer Anwendung instanziieren können. Diese Klassen werden im folgenden Speicherort generiert: \\<Windows-\>Verzeichnis \Java\trustlib\msado15.  
  
 Das Erstellen einer ADO-Anwendung in Java mithilfe des Microsoft SDK für Java ist von der Perspektive des Quellcodes über die Verwendung des Assistenten für die Java-Typbibliothek grundlegend identisch. Beispielcode finden Sie unter [ADO Java Class Wrapper](../../../ado/guide/appendixes/ado-java-class-wrappers.md). Der einzige wirkliche Unterschied besteht darin, wie Sie zuerst die Wrapper Klassen generieren, wie in den folgenden Schritten gezeigt.  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>So erstellen Sie ein ADO-Projekt mit dem Microsoft SDK für Java  
  
1.  Führen Sie den folgenden Befehl an einer Eingabeaufforderung aus. Sie müssen den Pfad so festlegen, dass das Verzeichnis "Microsoft SDK für Java bin" enthalten ist, oder Sie können den Befehl von diesem Speicherort aus ausführen. Das Microsoft SDK für Java wird in der Regel am gleichen Speicherort wie Visual Studio installiert. Dies ist eine einzelne Befehls Anweisung.  
  
    ```java
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  Führen Sie den folgenden Befehl aus, um die generierten Klassen zu kompilieren. Der Schalter/g: t schaltet die Generierung von Debugsymbolen, sodass Sie eine Ablauf Verfolgung in durchführen können. Java-Symbole. Entfernen Sie es für Releasebuilds.  
  
    ```java
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  Öffnen Sie das Projekt in Visual J++, um diese Dateien zu verwenden. Wählen Sie im Menü **Projekt** die Option **zu Projekt hinzufügen**aus. Wählen Sie **Dateien**aus, und fügen Sie alle hinzu. Java-Dateien, die im Verzeichnis trustlib\msado15 für Ihr Projekt generiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Java-Klassen-Wrapper](../../../ado/guide/appendixes/ado-java-class-wrappers.md)   
