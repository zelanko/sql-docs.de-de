---
title: Zwischenspeichern von Vorlagen (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 66c73c84a54daeeb2cca82e6b591da73b76a280b
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703300"
---
# <a name="template-caching-sqlxml-40"></a>Zwischenspeichern von Vorlagen (SQLXML 4.0)
  Das Zwischenspeichern von Vorlagen verbessert die Leistung erheblich. Wenn das Zwischenspeichern von Vorlagen festgelegt ist, verbleibt die Vorlage nach ihrer ersten Ausführung im Arbeitsspeicher. Auf diese Weise wird die Leistung der nächsten Vorlagenausführung verbessert.  
  
 Sie können die Cachegröße für Vorlagen festlegen, indem Sie den folgenden Schlüssel in der Registrierung hinzufügen:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Die Größe sollte auf Basis des vorhandenen Arbeitsspeichers und der Anzahl der von Ihnen verwendeten Vorlagen festgelegt werden. Der Standardwert für die **TemplateCacheSize** -Größe ist 31. Sie können die Cachegröße erhöhen, wenn der Vorlagenzugriff langsam erscheint, oder die Cachegröße verringern, wenn der Arbeitsspeicher zu gering ist.  
  
 Um eine bessere Leistung zu erzielen, empfiehlt es sich, **TemplateCacheSize** auf eine höhere Anzahl von Vorlagen festzulegen, die Sie normalerweise verwenden. Wenn **temlatecachesize** kleiner ist als die Anzahl der Vorlagen, die Sie besitzen, wird die Leistung beeinträchtigt, wenn sich die Anzahl der Vorlagen erhöht. **TemplateCacheSize** kann auf ein Maximum von 128 festgelegt werden.  
  
 Jedes Mal, wenn eine zwischengespeicherte Vorlage verwendet wird, wird die Änderungszeit der Vorlagendatei überprüft, um festzustellen, ob sie aktualisiert werden muss. Das liegt daran, dass die Datenträgerkopie neuer als die Cachekopie ist.  
  
> [!NOTE]  
>  Vorlagenparameter und Befehlseigenschaften werden nicht zwischengespeichert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Caching &#40;SQLXML 4,0&#41;](schema-caching-sqlxml-4-0.md)   
 [XSL-Caching &#40;SQLXML 4,0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  
