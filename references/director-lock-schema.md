# DIRECTOR_LOCK v1 输出合同

输出只描述导演决策，不写任何模型的最终提示词。`DIRECTOR_LOCK v1` 是合同族名称，`version` 记录兼容版本。使用 Markdown 表格或 YAML 均可，但字段不得省略。

## 顶层

```yaml
DIRECTOR_LOCK:
  contract_family: "DIRECTOR_LOCK v1"
  version: "1.3"
  schema_variant: "codex-director-lock"
  commercial_contract: {applicable: false, reason: "非商业任务"}
  director_lock_id: ""
  project:
    title: ""
    target_duration: 0.0
    aspect_ratio: ""
    frame_rate_assumption: ""
  SCRIPT_LOCK:
    script_lock_id: ""
    immutable_plot_facts: []
    immutable_relationships: []
    immutable_dialogue_meaning: []
    immutable_event_order: []
    must_keep: []
    must_avoid: []
  director_book:
    audience_state_A: ""
    audience_state_B: ""
    visual_thesis: ""
    primary_visual_anchor:
      object_or_event: ""
      entry: ""
      evolution: ""
      endpoint: ""
    physical_verb: ""
    spatial_system: ""
    visual_rule: ""
    selected_methods: []
    performance_register: ""
    camera_grammar: ""
    lighting_logic: ""
    sound_logic: ""
    editing_logic: ""
    mute_view_contract:
      verdict: pass|partial|fail
      visible_core_message: ""
      sound_only_information: []
      repair_required: []
  continuity_invariants: []
  reference_registry: []
  shots: []
  total_timing_check: {}
  resource_dependencies: []
  transfer_limits: []
  unresolved_risks: []
  lock_status: locked|blocked
```

## 每镜字段

```yaml
- shot_id: "S01"
  program_time: {in: 0.0, out: 0.0, duration: 0.0}
  story_function: ""
  audience_delta: ""
  audience_state_in: ""
  audience_state_out: ""
  visual_anchor: {object_or_event: "", meaning: "", reveal: "", evolution: "", endpoint: ""}
  expression_design: {task: "", mode: "", target: "", carrier: "", shared_relation: "", visible_mapping: "", intended_reading: "", alternative_reading: "", claim_boundary: ""}
  dramatic_beat: ""
  performance:
    objective: ""
    obstacle: ""
    tactic: ""
    trigger: ""
    listening_reaction: ""
    playable_behavior: ""
    state_in: ""
    state_out: ""
  blocking:
    start: ""
    motion: ""
    end: ""
    eyeline: ""
    distance_power_change: ""
  camera:
    shot_size: ""
    lens_and_distance: ""
    height_angle: ""
    position_orientation: ""
    composition_depth: ""
    focus_subject_and_transition: ""
    movement_reason: ""
    start_trigger: ""
    path: ""
    speed_phase: ""
    endpoint: ""
  lighting: {source: "", direction: "", information_change: "", endpoint: ""}
  sound: {bed: "", synced: [], silence: "", bridge: ""}
  dialogue: {speaker: "", exact_text: "", delivery: "", lip_sync_required: false}
  edit: {cut_motivation: "", transition_in: "", transition_out: ""}
  continuity: {screen_direction: "", prop_state: "", wardrobe_state: "", inherited: []}
  mute_view_test: {verdict: pass|partial|fail, visible_message: "", missing_without_sound: []}
  resource_dependencies: []
  transfer_limits: []
  timing: {}
  generation_units:
    - unit_id: "S01-U1"
      shot_ids: ["S01"]
      scope: ""
      duration_target: 0.0
      start_state: ""
      current_action: ""
      endpoint: ""
      completed_beats: []
      reserved_beats: []
      do_not_show: []
      actor_track: {duration: 0.0, evidence: ""}
      dialogue_track: {duration: 0.0, evidence: ""}
      camera_track: {duration: 0.0, evidence: ""}
      sound_track: {duration: 0.0, evidence: ""}
      serial_transitions: []
      timing_evidence: {t_min: 0.0, fit: pass|blocked}
      blocking_contract: {}
      camera_contract: {}
      sound_contract: {}
      dialogue_contract: {}
      references_needed: []
      allowed_changes: []
      preservation_locks: []
      risks: []
```

## 最终对账

```yaml
total_timing_check:
  shot_count: 0
  generation_unit_count: 0
  performance_beat_count: 0
  planned_total: 0.0
  target_total: 0.0
  gaps: []
  overlaps: []
  overloaded_shots: []
  dialogue_evidence: ""
```

三个数量不得互相替代。一个生成单元可以服务一个镜头，也可以在导演明确许可时为若干相邻镜头提供连续素材，所以必须用 `shot_ids` 明示归属。`lock_status: locked` 只在时间轴连续、每镜满足最低时长、剧情事实未变、所有生成单元都有 `start_state → current_action → endpoint`、四条时间轨与串行转换证据、主视觉锚点有明确终态、静音测试有真实结论时使用。

## 简例

剧本事实：“她递出辞职信；领导没有接；她把信放在桌上离开。”导演可以决定领导以沉默拖延、她先保持礼貌再停止等待、镜头在两人距离改变时收紧；不得改成领导批准、撕信或追出去。

```yaml
shot_id: S01
story_function: 让递交从请求转为单方面决定
audience_delta: 观众确认她不再等待许可
performance:
  objective: 让对方接收决定
  obstacle: 对方用沉默拒绝承认
  tactic: 从礼貌等待改为结束等待
  trigger: 对方持续不接
  playable_behavior: 保持递出状态，评估后收回等待，把信放下
blocking:
  start: 两人隔桌，信在两人之间
  motion: 她是唯一移动者；领导保持坐姿
  end: 信留在桌面，她退出双方共享空间
camera:
  movement_reason: 她的行为从请求变为决定时，观众需要看清权力转移
  endpoint: 停在她离开后仍留在两人之间的信
```

## 1.3 商业扩展与兼容

保留上述1.2全部字段与嵌套结构，仅增加 `schema_variant` 和 `commercial_contract`。商业、KOC、多资产任务按 [commercial-proof-contract.md](commercial-proof-contract.md) 填写扩展。非商业任务明确 applicable=false 与原因，不要求营销字段。`locked` 表示导演决策就绪，不等于资产已验收、能力已验证、付费已批准或成片已通过。

Hermes 的同名1.3使用不同结构，不能只改版本号：其 immutable_facts→SCRIPT_LOCK、audience_change/visual_thesis→director_book、duration_loads→四轨证据只是迁移线索；缺失 generation_units、镜头时码或声源决定必须由导演层补齐并重新锁定。未知变体不得直接编译。

旧Codex 1.2非商业锁可按原结构直接验证使用；商业、KOC或精确多资产旧锁由导演补齐扩展并重新锁定。不得由编译器填applicable=false跳过真实商业要求。

## 2.1 表达与摄影增量

新导演输出记录expression_design与camera新增三字段，沿用合同1.3的可选扩展机制，不改既有字段含义。直接表达的carrier/shared_relation可标不适用并给原因。STATIC的path写固定、start_trigger写起镜保持、endpoint写实际终框；焦点明确固定或转移。旧锁若已在其他字段明确这些决定可无损映射；缺失关键摄影决定由导演层补齐，编译器不能猜。未生成的静音与表达判断标为预判。

## 2.2 决策衔接（保持结构1.3）

不增加必填字段。表达支点写入 `director_book.visual_thesis` 和每镜 `expression_design.target/shared_relation`；实际关系落到 `blocking`、`camera.movement_reason/composition_depth`、`sound` 与 `edit.cut_motivation`。声音的空间路线可写入 `sound.bed/synced/bridge` 中对应的文字描述。各字段共享同一决定，避免概念说释放、画面却继续压缩而无解释。无人物任务的performance字段注明不适用；稳定画面允许blocking.motion为保持、由声音承担变化。

检查时沿“表达目标→可感知关系→执行决定→预期感受”追溯一次；不能仅检查字段非空。保持prompt-skill已有输入结构与权限，不让编译器补导演决定。
