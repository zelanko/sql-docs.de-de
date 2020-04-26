---
title: Identifizieren der Quelle von Paketen mit digitalen Signaturen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing packages [Integration Services]
- certificates [Integration Services]
- packages [Integration Services], security
- security [Integration Services], certificates
- signing policies [Integration Services]
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 714ede33a89a3ab4e44dae682887ee0c21c9f363
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62766652"
---
# <a name="identify-the-source-of-packages-with-digital-signatures"></a>Identifizieren der Quelle von Paketen mit digitalen Signaturen
  Ein [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket kann mit einem digitalen Zertifikat signiert werden, um seine Quelle zu identifizieren. Nachdem das Paket mit einem digitalen Zertifikat signiert wurde, können Sie die digitale Signatur vor dem Laden des Pakets mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] überprüfen. Damit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] die Signatur prüft, legen Sie eine Option entweder in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder im **dtexec** -Hilfsprogramm (dtexec.exe) fest, oder geben Sie einen optionalen Registrierungswert an.  
  
## <a name="signing-a-package-with-a-digital-certificate"></a>Signieren eines Pakets mit einem digitalen Zertifikat  
 Bevor Sie ein Paket mit einem digitalen Zertifikat signieren können, müssen Sie zunächst ein Zertifikat abrufen oder erstellen. Sobald Sie das Zertifikat vorliegen haben, können Sie es zum Signieren des Pakets verwenden. Weitere Informationen zum Abrufen eines Zertifikats und zum Signieren eines Pakets mit diesem Zertifikat finden Sie unter [Signieren eines Pakets mit einem digitalen Zertifikat](../sign-a-package-by-using-a-digital-certificate.md).  
  
## <a name="setting-an-option-to-check-the-package-signature"></a>Festlegen einer Option zum Überprüfen der Paketsignatur  
 Sowohl [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] als auch das **dtexec** -Hilfsprogramm bieten eine Option, mit der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] für die Überprüfung der digitalen Signatur eines signierten Pakets konfiguriert wird. Ob Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder das **dtexec** -Hilfsprogramm verwenden, hängt davon ab, ob Sie alle Pakete oder nur bestimmte Pakete überprüfen möchten:  
  
-   Wählen Sie die Option **Digitale Signatur beim Laden eines Pakets überprüfen** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aus, um die digitale Signatur aller Pakete vor dem Laden der Pakete zum Entwurfszeitpunkt zu überprüfen. Diese Option ist eine globale Einstellung für alle Pakete in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Weitere Informationen finden Sie unter [General Page](../general-page-of-integration-services-designers-options.md).  
  
-   Um die digitale Signatur eines einzelnen Pakets zu überprüfen, geben `/VerifyS[igned]` Sie die Option an, wenn Sie das Paket mit dem Hilfsprogramm **dtexec** ausführen. Weitere Informationen finden Sie [hier](../packages/dtexec-utility.md).  
  
## <a name="setting-a-registry-value-to-check-the-package-signature"></a>Festlegen eines Registrierungswerts zum Überprüfen der Paketsignatur  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] unterstützt außerdem den optionalen Registrierungswert **BlockedSignatureStates**, mit dem Sie die Richtlinie einer Organisation zum Laden von signierten und nicht signierten Paketen verwalten können. Der Registrierungswert kann das Laden von Paketen verhindern, wenn die Pakete nicht signiert sind, oder ungültige oder nicht vertrauenswürdige Signaturen enthalten. Weitere Informationen zum Festlegen des Registrierungswerts finden Sie unter [Implementieren einer Signaturrichtlinie durch Festlegen eines Registrierungswerts](../implement-a-signing-policy-by-setting-a-registry-value.md).  
  
> [!NOTE]  
>  Der optionale Registrierungswert **BlockedSignatureStates** kann eine Einstellung angeben, die restriktiver ist als die Option für die digitale Signatur, die in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder in der **dtexec**-Befehlszeile festgelegt wurde. In dieser Situation überschreibt die restriktivere Registrierungseinstellung die andere Einstellung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Paketen](../integration-services-ssis-packages.md)   
 [Sicherheitsübersicht &#40;Integration Services&#41;](security-overview-integration-services.md)  
  
  
