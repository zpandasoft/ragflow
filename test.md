## 1. 概要
光伏组件出口到法国ESG合规要求agent
## 2. 核心流程
 ### 2.1 政策法规收集-不限方式
    获取光伏组件出口法国的必须政策文件
 ### 2.2 构建知识库
    目标：将收集到的政策法规整理成结构化的知识库，便于查询和使用。
    实现方法：
        文本处理：多类型文档解析。
        分类整理：利用主题建模技术（如LDA），按照ESG三大维度（环境、社会、治理）对政策进行分类。
        结构设计：构建知识图谱，连接政策文本、关键词和主题，提高检索效率。
        
    知识库结构示例：
        政策文本：完整法规内容或摘要
        关键词：光伏、ESG、合规、法国、欧盟
        知识图谱：
        主题分类：
            环境：碳足迹、废弃物管理
            社会：供应链责任
            治理：信息披露要求
### 2.3 合规步骤生成agent
    目标：生成光伏组件出口到法国的具体合规步骤以及步骤依据。
         生成每个步骤所需要都具体内容细则以及细则依据。

```mermaid
sequenceDiagram
    participant User as 用户
    participant QU as 查询理解模块
    participant KR as 知识检索Agent
    participant CA as 合规分析Agent
    participant RV as 推理验证Agent
    participant SG as 步骤生成Agent
    participant OF as 输出格式化模块
    
    User->>QU: 光伏组件出口到法国需要完成哪些ESG合规要求？
    
    QU->>QU: 分析查询理解意图
    Note over QU: 提取关键词: 光伏组件, 法国, ESG, 合规要求
    Note over QU: 推断查询目的: 获取完整合规步骤
    
    QU->>KR: 传递结构化查询
    
    KR->>KR: 执行多模态检索
    Note over KR: 1. 检索法国特定光伏法规
    Note over KR: 2. 检索欧盟通用ESG法规
    Note over KR: 3. 检索光伏行业标准
    Note over KR: 4. 检索相关案例
    
    KR-->>CA: 返回相关法规和标准(约15项)
    
    CA->>CA: 合规要求分析
    Note over CA: Step 1: 将法规分类(环境/社会/治理)
    Note over CA: Step 2: 提取每类中的强制性要求
    Note over CA: Step 3: 分析要求间的依赖关系
    Note over CA: Step 4: 形成合规政策列表
    
    CA-->>RV: 提交分析结果(7项合规政策)
    
    RV->>RV: 执行验证
    Note over RV: 验证1: 是否涵盖所有关键法规?
    Note over RV: 验证2: 政策描述是否准确?
    Note over RV: 验证3: 是否存在最新更新?
    Note over RV: 发现问题: 碳足迹计算标准更新
    
    RV->>KR: 请求额外信息
    KR-->>RV: 返回最新法规更新
    
    RV->>RV: 修正分析结果
    RV-->>SG: 传递验证后的合规政策
    
    SG->>SG: 步骤规划和生成
    Note over SG: 步骤1: 根据优先级排序
    Note over SG: 步骤2: 分解为具体操作
    Note over SG: 步骤3: 添加法规依据
    Note over SG: 步骤4: 补充所需文档
    Note over SG: 步骤5: 生成验证方法
    
    SG-->>OF: 提交生成的步骤(7项主步骤,23项子步骤)
    
    OF->>OF: 格式化输出内容
    OF-->>User: 返回结构化合规要求和步骤
```

### 2.4 步骤以及细则审核
    考虑到AI的幻觉以及所属业务为付费产品的原因，本着对结果负责的宗旨需要对生成的步骤以及细则进行审核。
    用户看到的均为审核后的数据
### 2.5 根据审核后的细则收集完成细则所需要的数据收集与计算agent

```mermaid
sequenceDiagram
    participant User as 用户
    participant DRA as 数据需求分析Agent
    participant DSA as 数据源分析Agent
    participant DCA as 数据收集Agent
    participant DPA as 数据处理Agent
    participant CMA as 计算方法分析Agent
    participant DQA as 数据质量验证Agent
    participant OF as 输出格式化模块
    
    User->>DRA: 提交审核后的合规细则
    
    DRA->>DRA: 分析数据需求
    Note over DRA: 1. 识别必要数据项
    Note over DRA: 2. 确定数据类型与格式
    Note over DRA: 3. 建立数据依赖关系图
    Note over DRA: 4. 区分原始数据与计算数据
    
    DRA-->>DSA: 传递数据需求清单
    
    DSA->>DSA: 数据源分析
    Note over DSA: 1. 识别内部可用数据源
    Note over DSA: 2. 识别外部公开数据源
    Note over DSA: 3. 识别需要企业提供的数据
    Note over DSA: 4. 评估数据源可靠性
    
    DSA-->>DCA: 传递数据源映射方案
    
    DCA->>DCA: 执行数据收集
    Note over DCA: 1. 构建API调用策略
    Note over DCA: 2. 设计表单收集方案
    Note over DCA: 3. 实施数据抓取计划
    Note over DCA: 4. 记录数据来源与时间戳
    
    DCA-->>DPA: 传递原始数据集
    
    DPA->>DPA: 数据处理与转换
    Note over DPA: 1. 数据清洗与标准化
    Note over DPA: 2. 数据格式转换
    Note over DPA: 3. 缺失值处理
    Note over DPA: 4. 异常值检测与处理
    
    DPA-->>CMA: 传递处理后数据集
    
    CMA->>CMA: 计算方法分析与执行
    Note over CMA: 1. 识别计算公式与标准
    Note over CMA: 2. 确定计算依赖关系
    Note over CMA: 3. 执行计算流程
    Note over CMA: 4. 生成计算结果与证据
    
    CMA-->>DQA: 传递计算结果与原始数据
    
    DQA->>DQA: 数据质量验证
    Note over DQA: 1. 完整性验证
    Note over DQA: 2. 准确性验证
    Note over DQA: 3. 一致性验证
    Note over DQA: 4. 合规性验证
    
    DQA-->>OF: 传递验证后的完整数据包
    
    OF->>OF: 格式化输出内容
    OF-->>User: 返回结构化数据与计算结果
```

    
### 2.6 数据完整性验证与审核

### 2.7 整合最终方案形成报告等


## 3. 子流程

### 3.1 自动化爬虫
     自动化爬虫获取相关政策法规数据
     详见：大模型辅助构建 ESG 合规知识库设计理念与使用说明.docx
 ![系统架构图](architecture_diagram.svg)

## 4. 实施步骤
 ### 4.1 方案一:  知识库 --> 合规步骤生成agent -->自动化爬虫
     先使用现有爬虫、手动等方式获取光伏组件出口法国的必须政策文件
     基于文件完成核心流程的研究与开发。
     基于核心流程以及公司客户主要业务目标完成初始版本交付

 目标:先完成核心流程保证有一个可用的产品，然后完善子流程及优化
 好处：只要核心流程完成即可交付初始版本以供其他团队使用，
      可避免若核心流程未完成，那么爬虫设计的再好也不能交付或者爬虫流程未完成则无任何可交付物的风险，
      积累所需爬取数据的初步流程与方法

### 4.2 方案二: 自动化爬虫 -->  知识库 --> 合规步骤生成agent
风险:周期长，若爬虫未完成则无任何可交付物