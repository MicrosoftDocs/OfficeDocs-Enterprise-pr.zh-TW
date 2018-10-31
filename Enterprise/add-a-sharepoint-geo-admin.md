---
title: 新增或移除異地系統管理員
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解如何在新增或移除的地理位置管理員 OneDrive for Business 多-地理位置。
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849809"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="45b19-103">新增或移除的地理位置管理員的 onedrive for Busniess 多-地理位置</span><span class="sxs-lookup"><span data-stu-id="45b19-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="45b19-p101">您可以設定不同的系統管理員必須在您的租用戶中每個地理位置。這些系統管理員必須 SharePoint Online 和 OneDrive 設定所特有及其地理位置的存取權。</span><span class="sxs-lookup"><span data-stu-id="45b19-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="45b19-p102">某些服務-例如之字詞儲存區-是從集中管理位置管理並複寫至衛星位置。集中管理位置地理系統管理員具有存取這些，而衛星位置的地理位置 admins 不。</span><span class="sxs-lookup"><span data-stu-id="45b19-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="45b19-108">全域管理員與 SharePoint Online 管理員繼續執行集中管理位置和附屬的所有位置中設定的存取權。</span><span class="sxs-lookup"><span data-stu-id="45b19-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="45b19-109">設定地理管理員</span><span class="sxs-lookup"><span data-stu-id="45b19-109">Configuring geo administrators</span></span>

<span data-ttu-id="45b19-110">設定地理 admins 需要 SharePoint Online PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="45b19-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="45b19-111">使用[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)連線至系統管理中心的地理位置您要新增地理位置管理]。（例如 Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="45b19-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="45b19-112">若要檢視現有地理 admins 的位置，請執行`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="45b19-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="45b19-113">將使用者新增為地理位置管理</span><span class="sxs-lookup"><span data-stu-id="45b19-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="45b19-114">若要將使用者新增為地理位置管理、 執行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="45b19-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="45b19-115">若要移除使用者以地理位置的系統管理員位置、 執行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="45b19-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="45b19-116">新增的地理位置系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="45b19-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="45b19-117">您可以將安全群組或擁有郵件功能的安全性群組新增為地理位置管理]。（通訊群組與 Office 365 群組不支援。）</span><span class="sxs-lookup"><span data-stu-id="45b19-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="45b19-118">若要將群組新增地理系統管理員身分、 執行`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="45b19-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="45b19-119">若要移除群組地理系統管理員身分執行`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="45b19-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="45b19-p103">請注意不是所有安全性群組都有群組的別名。如果您想要新增安全性群組沒有指定別名，執行[Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup)來擷取群組的清單，尋找您安全性群組 ObjectID，然後執行：</span><span class="sxs-lookup"><span data-stu-id="45b19-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="45b19-122">若要移除群組使用 ObjectID、 執行`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="45b19-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="45b19-123">存取特定的地理位置的系統管理中心</span><span class="sxs-lookup"><span data-stu-id="45b19-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="45b19-124">若要管理其地理位置的 OneDrive 設定，系統管理員必須存取 OneDrive 系統管理中心直接使用 URL 格式如下：</span><span class="sxs-lookup"><span data-stu-id="45b19-124">To administer OneDrive settings for their geo location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="45b19-125">https://admin.onedrive.com/?geo=<*地理位置*></span><span class="sxs-lookup"><span data-stu-id="45b19-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="45b19-126">例如，加拿大 OneDrive 系統中心位於： https://admin.onedrive.com/?geo=CAN。</span><span class="sxs-lookup"><span data-stu-id="45b19-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="45b19-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45b19-127">See Also</span></span>

[<span data-ttu-id="45b19-128">新增 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="45b19-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="45b19-129">取得 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="45b19-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="45b19-130">移除 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="45b19-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="45b19-131">設定別名 (MailNickName) 的安全性群組</span><span class="sxs-lookup"><span data-stu-id="45b19-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)