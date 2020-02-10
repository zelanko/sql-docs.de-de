---
title: Geschäftsregelaktionen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cdc4daca-3dff-46d8-b7f0-57f7826dd61a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 83e65825f098dbcabe9fa6cbb67513e1c9654f9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483628"
---
# <a name="business-rule-actions-master-data-services"></a>Geschäftsregelaktionen (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]sind Geschäftsregelaktionen die Folge von Geschäftsregel-Bedingungsauswertungen. Wenn eine Bedingung erfüllt ist (TRUE), wird die Aktion initiiert.  
  
> [!NOTE]  
>  Für Standardwert- und Wertänderungsaktionen wird der generierte Wert abgeschnitten, falls er die maximale Attributlänge überschreitet.  
  
## <a name="default-value-actions"></a>Standardwertaktionen  
 **Standardwert** Aktionen legen den Standardwert eines angegebenen Attributs fest. Benutzer mit entsprechender Berechtigung können diese Standardwerte ändern.  
  
|Wertname|BESCHREIBUNG|  
|----------------|-----------------|  
|**Standardwert**|Das ausgewählte Attribut **entspricht standardmäßig** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**Standardwert für einen generierten Wert**|Das ausgewählte Attribut **entspricht standardmäßig einem generierten Wert** , der durch Eingabe eines Startwerts und eines inkrementellen Werts bestimmt wird.<br /><br /> Diese Aktion ist für Text- und Nummernwerte gültig.|  
|**entspricht standardmäßig einem verketteten Wert**|Das ausgewählte Attribut **entspricht standardmäßig einem verketteten Wert** , der durch Angabe mehrerer Attribute bestimmt wird.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
  
## <a name="change-value-actions"></a>Wertänderungsaktionen  
 Aktionen zum **Ändern von Werten** aktualisieren den Wert eines angegebenen Attributs oder Attribut Werts. Benutzer können diese Werte nur ändern, wenn der neue Wert bewirkt, dass die Aktion TRUE ergibt.  
  
|Wertname|BESCHREIBUNG|  
|----------------|-----------------|  
|**Aufbauen**|Das ausgewählte Attribut wird in einen definierten Attributwert oder ein anderes Attribut geändert bzw. ist leer.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**gleicht einen verketteten Wert**|Das ausgewählte Attribut wird in einen verketteten Wert geändert, der durch Angabe mehrerer Attribute bestimmt wird.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
  
## <a name="validation-actions"></a>Überprüfungsaktionen  
 Wenn Sie **Validierungs** Aktionen nicht als true auswerten, senden Sie eine e-Mail an einen bestimmten Benutzer oder eine bestimmte Gruppe. Um für eine Version einen Commit auszuführen, müssen alle Überprüfungsaktionen TRUE ergeben.  
  
 Die einzigen Ausnahmen sind die Aktionen **ist verbindlich** und **ist ungültig** . Diese Aktionen müssen mit einer Aktion zum Ändern von Werten kombiniert werden, damit die Daten erfolgreich überprüft werden können und ein Commit für die Version ausgeführt werden kann.  
  
|Name der Überprüfung|BESCHREIBUNG|  
|---------------------|-----------------|  
|**ist erforderlich**|Das ausgewählte Attribut **ist erforderlich**, es kann also nicht NULL lauten oder leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**ist ungültig**|Das ausgewählte Attribut **ist ungültig**.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**muss das Muster enthalten**|Das ausgewählte Attribut **muss das Muster enthalten** , das angegeben ist. Verwenden Sie reguläre Ausdrücke von .NET Framework, um das Muster anzugeben.<br /><br /> Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre](https://go.microsoft.com/fwlink/?LinkId=164401) Ausdrücke in der MSDN Library.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
|**muss eindeutig sein**|Das ausgewählte Attribut **muss eindeutig sein** , und zwar unabhängig von definierten Attributen oder in Kombination mit ihnen.<br /><br /> **Bewährte Methoden:** Kombinieren Sie diese Aktion mit einer obligatorischen Bedingung, um die Gültigkeit der Indexfelder in Abonnement Systemen sicherzustellen.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**muss einen der folgenden Werte aufweisen:**|Das ausgewählte Attribut **muss einen der folgenden Werte aufweisen** , die in einer Liste angegeben sind.<br /><br /> Diese Aktion ist für Textwerte gültig.|  
|**muss größer sein als**|Das ausgewählte Attribut **muss größer sein als** ein bestimmtes Attribut oder ein bestimmter Attributwert bzw. muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**muss gleich sein**|Das ausgewählte Attribut **muss gleich sein** , und zwar mit einem definierten Attributwert oder einem anderen Attribut bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**muss größer als oder gleich sein**|Das ausgewählte Attribut **muss größer als oder gleich sein** , und zwar mit einem bestimmten Attribut oder Attributwert bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**muss kleiner sein als**|Das ausgewählte Attribut **muss kleiner sein als** ein bestimmtes Attribut oder ein bestimmter Attributwert bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**muss kleiner als oder gleich sein**|Das ausgewählte Attribut **muss kleiner als oder gleich sein** , und zwar mit einem bestimmten Attribut oder Attributwert bzw. es muss leer sein.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**muss zwischen**|Das ausgewählte Attribut **muss liegen zwischen** zwei bestimmten Attributen oder Attributwerten.<br /><br /> Diese Aktion ist für Text-, Zahlen- und Datumswerte gültig.|  
|**muss eine Mindestlänge haben von**|Das ausgewählte Attribut **muss eine Mindestlänge haben vom** angegebenen Wert.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
|**muss eine maximale Länge aufweisen.**|Das ausgewählte Attribut **muss eine Höchstlänge haben vom** angegebenen Wert.<br /><br /> Diese Aktion ist für Text- und Linkwerte gültig.|  
  
## <a name="external-action"></a>Externe Aktion  
 **Externe** Aktionen interagieren mit Anwendungen außerhalb von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
|Aktionsname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**Workflow starten**|Initiiert einen externen Workflow. Die Daten, die diese Aktion bewirkt haben, werden an den Workflow übergeben. Weitere Informationen finden Sie unter [SharePoint Workflow Integration with Master Data Services](https://msdn.microsoft.com/library/gg690195.aspx).<br /><br /> Diese Aktion ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Geschäftsregel Bedingungen &#40;Master Data Services&#41;](business-rule-conditions-master-data-services.md)   
 [Master Data Services von Geschäftsregeln &#40;&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)  
  
  
