# 商业主张、KOC 与多资产合同

仅在商业主张、KOC 插片或精确多资产展示时读取。导演负责决定，编译器只翻译。

## 条件扩展结构

```yaml
commercial_contract:
  applicable: true
  claims:
    - claim_id: C01
      exact_claim: 公司拥有多份检测资料
      owner_type: company
      owner_id: COMPANY01
      evidence_assets: [DOC01]
      evidence_scope: 公司资料集合，不代表当前单品功效
      allowed_inference: 存在这些真实文件
      forbidden_inference: 当前单品拥有整个公司的全部检测报告
      status: verified
  shot_proofs:
    - shot_id: S01
      claim_ids: [C01]
      proof_task: 看清资料集合的真实存在及归属
      evidence_identity: real_asset
      visible_result: 真实资料在稳定终框可辨
      protected_regions: [文件身份区域]
  koc_inserts: []
  truth_boards: []
```

owner_type 使用 company/brand/product_family/product；status 使用 verified/pending/unsupported。verified 只表示已对当前源材料核验范围，不表示法律、效果或投放验收。evidence_identity 使用 real_asset/demonstration/illustration/reenactment/generated。示意和生成画面不能提升为实测证明。口播、屏幕文字、视觉暗示三轨都要与归属一致。无材料时不虚填 verified。

## KOC 插片（存在时必填）

每项包含 insert_id、shot_ids、entry_trigger、proof_task、voice_continuity、exit_trigger、return_frame。voice_continuity 写 speaker、exact_text、audio_interval、source_in/source_during/source_out、no_repeat；同一句以同一音频区间贯穿，切镜不重复台词。return_frame 锁达人身份、景别、视线、产品位置与声源。画面中人物闭嘴但合同指定画外声时保留该决定。

## 静态真值板（需要精确数量或区别时必填）

每板包含 board_id、asset_version、approval_status(pending/approved)、expected_unique_count、slots。每槽包含 slot_id、asset_id、asset_version、source_identity、content_fingerprint、owner_id、role、text_disposition。文件页面的 source_identity=稳定源文件标识+页码；产品的 source_identity=真实产品/变体标识。要求slot_id唯一，按真实source_identity去重计数等于expected_unique_count，并核对内容指纹：同页复制或另起asset_id别名不创造不同页面；同PDF不同页可分别计数。不同文件内容相同不算不同页面，但可在有证据时分别计为不同报告；合同必须明确count_unit是page、document还是product_variant。每份素材存在且与claim owner/scope相符。允许重复展示同一产品时显式写重复职责，不能将重复计入唯一数量。

先验证静态布局、遮挡和最终裁切可读性，再让视频生成运动。真实页面精确文本与数字优先保留真实资产或后期合成；不把‘20张不同页面’交给模型自行复制编造。板只是布局控制，不证明模型能保住每一页；成片另验数量、身份与文字。

## 验收与授权

证明机位保护接触、标签、状态变化和终态；审美机位可服务气氛，但不替代证据。现有用户授权覆盖的准备、生成或修改继续执行；只有超出已授权范围的实质动作才请求补充许可。内部审阅、文件锁定、用户批准和成片验收是不同状态。

## 示例边界

公司有20份资料、当前单品仅关联2份：可以在归属清晰且不暗示单品20份的情况下展示公司集合；要证明单品则仅绑定2份。用户锁定20页且材料只有2页时，记录缺18份真实资产，先完成时码与布局方案，不复制页面、不改变口播归属、不宣称素材就绪。
