---
title: 從商務用 Skype 與 Exchange 移除或停用混合式新式驗證
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 如果您已啟用混合式新式驗證（HMA），而只是找出它不適用於您目前的環境，您可以停用 HMA。 本文說明如何進行。
ms.openlocfilehash: ad9db5894670b49d2d9a1f385cd9f6acd43ea00f
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998202"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="aa66e-104">從商務用 Skype 與 Exchange 移除或停用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="aa66e-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="aa66e-105">*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="aa66e-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="aa66e-106">如果您已啟用混合式新式驗證（HMA），而只是找出它不適用於您目前的環境，您可以停用 HMA。</span><span class="sxs-lookup"><span data-stu-id="aa66e-106">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="aa66e-107">本文說明如何進行。</span><span class="sxs-lookup"><span data-stu-id="aa66e-107">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="aa66e-108">本文的人選是誰？</span><span class="sxs-lookup"><span data-stu-id="aa66e-108">Who is this article for?</span></span>

<span data-ttu-id="aa66e-109">如果您已在商務用 Skype Online 或內部部署和/或 Exchange Online 或內部部署中啟用新式驗證，且找到您需要停用 HMA，這些步驟適用于您。</span><span class="sxs-lookup"><span data-stu-id="aa66e-109">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa66e-110">若您是在商務用 Skype Online 或內部部署中，請參閱「[新式驗證支援的商務用 skype 拓撲](https://technet.microsoft.com/library/mt803262.aspx)」文章，其具有混合拓撲 HMA，您必須先查看支援的拓撲，再開始。</span><span class="sxs-lookup"><span data-stu-id="aa66e-110">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="aa66e-111">如何停用混合式新式驗證（Exchange）</span><span class="sxs-lookup"><span data-stu-id="aa66e-111">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="aa66e-112">**Exchange 內部部署**：開啟 Exchange 管理命令介面，並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="aa66e-112">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="aa66e-113">**Exchange online**：以遠端 PowerShell[連接至 Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="aa66e-113">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="aa66e-114">執行下列命令，將您的*OAuth2ClientProfileEnabled*旗標轉換為 "false"：</span><span class="sxs-lookup"><span data-stu-id="aa66e-114">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="aa66e-115">如何停用混合式新式驗證（商務用 Skype）</span><span class="sxs-lookup"><span data-stu-id="aa66e-115">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="aa66e-116">**商務用 skype 內部部署**：在商務用 Skype 管理命令介面中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="aa66e-116">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="aa66e-117">**商務用 Skype online**：使用遠端 PowerShell[連接至商務用 skype online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="aa66e-117">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="aa66e-118">執行下列命令以停用新式驗證：</span><span class="sxs-lookup"><span data-stu-id="aa66e-118">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="aa66e-119">[連結回新式驗證概述](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="aa66e-119">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

