---
title: Mithilfe des Microsoft SDK für Java | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Java (Microsoft SDK for)
- Microsoft SDK for Java [ADO]
ms.assetid: 2d7cb5b5-8307-49dd-b07e-c07069bb1626
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: edab19ee8b3ae4eee186835d25220ee638c41149
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786918"
---
# <a name="using-the-microsoft-sdk-for-java"></a>Verwenden des Microsoft SDK für Java

> [!IMPORTANT]
> Microsoft unterstützt Visual J++ im Januar 2004.

Das Microsoft-SDK für Java ist das Entwicklerkit für die Microsoft Internet Explorer-Umgebung. Tools, Informationen und Beispiele werden bereitgestellt, können Sie die Entwicklung von Java-Programme und Applets, die basierend auf JDK 1.1 und die Microsoft Win32-VM (Microsoft VM). Das Microsoft-SDK für Java ist nicht mit Microsoft Visual J++ gebunden. Klicken Sie hier Informationen zum Herunterladen dieses SDKS.  
  
 Das Hilfsprogramm Jactivex.exe generiert Klassen aus einer Typbibliothek, aber es kann nur in der Befehlszeile aufgerufen werden. Dieses Feature ist nicht in die Entwicklungsumgebung Visual J++ integriert. Im Gegensatz zu den Klassen, die von der Java-Bibliothek-Assistenten generiert wird können Sie die Klassen-Wrapper, der vom SDK erstellten schrittweise. Dies ist nützlich für das Debuggen wie Ihr Code die ADO-Wrapperklassen verwendet.  
  
 Dieser Mechanismus liest die ADO-Typbibliothek und generiert Klassen, die Sie in Ihrer Anwendung instanziieren können. Diese Klassen werden am folgenden Speicherort generiert: \\< Windows-Verzeichnis\>\Java\trustlib\msado15.  
  
 Erstellen eine ADO-Anwendung in Java mithilfe von Microsoft SDK für Java ist im Grunde identisch, aus der Perspektive des Quellcodes, mit der Verwendung der Java-Bibliothek-Assistenten. Beispielcode, finden Sie unter [ADO-Java-Klassen-Wrapper](../../../ado/guide/appendixes/ado-java-class-wrappers.md). Der einzige wirkliche Unterschied ist, in das Generieren der Wrapper-Klassen im vornherein, wie in den folgenden Schritten veranschaulicht.  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>So erstellen Sie ein ADO-Projekt mit dem Microsoft-SDK für Java  
  
1.  Führen Sie Folgendes an der Eingabeaufforderung ein. Sie müssen den Pfad auf dem Microsoft SDK für Java-Bin-Verzeichnis enthalten oder führen Sie den Befehl von diesem Speicherort. Das Microsoft-SDK für Java ist in der Regel am gleichen Speicherort wie für Visual Studio installiert. Dies ist ein einzelner Befehl-Anweisung.  
  
    ```  
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  Führen Sie den folgenden Befehl aus, um die generierten Klassen zu kompilieren. Der /g:t Schalter aktiviert die Generierung von Debugsymbolen, damit Sie in die Ablaufverfolgung können der. Java-Symbole. Entfernen Sie sie für Releasebuilds.  
  
    ```  
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  Um diese Dateien zu verwenden, öffnen Sie Ihr Projekt in Visual J++. Von der **Projekt** Menü wählen **zu Projekt hinzufügen**. Wählen Sie **Dateien**, und Hinzufügen aller der. JAVA-Dateien im Verzeichnis trustlib\msado15 zu Ihrem Projekt generiert.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Java-Klassen-Wrapper](../../../ado/guide/appendixes/ado-java-class-wrappers.md)   
