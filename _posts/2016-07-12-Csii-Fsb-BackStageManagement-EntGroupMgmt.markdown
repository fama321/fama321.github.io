---
layout:     post
title:      "CSII-Project:FSB后管集团业务"
subtitle:   "集团设置"
author:     "Jiaming"
date:     2016-07-12 17:10:00 +0800  
header-img: "img/post-bg-android.jpg"
categories:    [CSII, FSB, Work]
tags:
    - CSII
    - FSB
    - Work
---

##公司集团关系设置

>企业客户 - 客户管理 - 集团关系管理

业务流程:

1. 根据证据信息查询母公司列表信息

  	**EntGroupSetList - ent.MCMEntGroupSetListQry**

2. 查询具体信息（包括集团关系信息）

 	**EntGroupSetInfo - ent.MCMEntGroupSetInfo**

   ***<font color=blue>ecif.cccifcustrel</font>***  --集团客户关联信息表，当前功能支持查询、定存、调拨等功能
   
3. **<font color=red>删除</font>** 

   **EntGroupSetDeletePre - ent.MCMEntGroupSetUpdatePre**   删除确认

   **EntGroupSetDelete - ent.MCMEntGroupSetDelete** 删除结果
	
		数据结构
		
		for accountlist:ac
		
			ecif.ecacct    --账户信息表
			
			ecif.ecacctrule    --账户规则表  用途不明
			
			ecif.ecacctmch    --账户渠道关联表
			
			ecif.eccifroleprdac    --角色权限  RoleSeq - PrdId - AcSeq - MakeRight - CheckRight
			
			ecif.eccifroleac    --角色账户关联表  RoleSeq - AcSeq
			
			ecif.shentacauth    --账户复核层级设置表 
			
			AcSeq - CifSeq - L1Count - L2Count - ... － BeginAmount - EndAmount
			
			ecif.shentusracauth    --用户层级限额设置 
			
			UserSeq - AcSeq - AuthLevel - MinAmount - MaxAmount
			
			
			ecif.ecusrmchacct    --已补充操作，待验证
		
		endfor
		
		ecif.ecusrcustrel    --集团用户关联表 CifSeq - UserSeq - RelCifNo - RelAcType - ...（权限字段）
		
		ecif.eccifcustrel    --集团客户关联表 CifSeq - RelCifNo - RelAcType

4. **<font color=red>修改</font>** 

   **EntGroupSetUpdatePre - ent.MCMEntGroupSetUpdatePre**   修改确认

   **EntGroupSetUpdate - ent.MCMEntGroupSetUpdate** 修改结果
   
   		数据结构
   		
   		ecif.ecusrcustrel
   		
   		ecif.eccifcustrel
   		
5. **<font color=red>新增</font>**
   
   **EntGroupSetInsertPre - ent.MCMEntGroupSetInsertPre**   新增校验

   **EntGroupSetInsert - ent.MCMEntGroupSetInsert** 新增结果
   
   		ecif.ecacct
   		
   		ecif.ecacctmch
   		
   		ecif.ecusrmchacct      #比删除步骤多此表操作
   		
   		ecif.ecacctrule
   		
   		ecif.eccifroleac
   		
   		ecif.eccifroleprdac
   		
   		ecif.shentacauth
   		
   		ecif.shentusracauth
   		
   		-------------------
   		
   		ecif.eccifcustrel