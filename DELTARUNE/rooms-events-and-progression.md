# Rooms, Events, and Progression

This catalog lists every room asset once and describes only the runtime role,
connections, controllers, and conditions that could be established.

The catalog contains all 1251 room assets exactly once: Chapter 1: 147, Chapter
2: 278, Chapter 3: 246, Chapter 4: 328, and Chapter 5: 252. Identically named
rooms in different payloads are separate records.

Statuses are: verified production reachable, conditional, bootstrap, debug-test,
and uncertain-no-ingress. The last means no ingress was found; it is not proof
that the room is unreachable.

“No additional condition verified” is an honest unknown, not proof that no gate
exists.

## Verified progression-state map

| Ch. | Area/event       | State              | Canonical source       |
| --- | ---------------- | ------------------ | ---------------------- |
| 1   | Jevil            | Flags 241/242      | Joker battle events    |
| 2   | Keyboard 1       | Flag 390           | Keyboard controller    |
| 3   | Sword board      | Plot + flag 1055   | Sword-route controller |
| 4   | Noelle basement  | Side B; plot 63→65 | Basement event         |
| 5   | West-cliff chest | Flags 468/142/571  | Treasure event         |

## Chapter 1 (147 assets)

### Chapter 1: `PLACE_CONTACT`

- Area: Player flow.
- Runtime role/status: contact or chapter-entry runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_CONTACT`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime variable
  dispatch to PLACE_CONTACT.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `PLACE_DOG`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `PROCESS_DOG`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 1: `PLACE_FAILURE`

- Area: Player flow.
- Runtime role/status: failure/game-over runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_FAILURE`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `PLACE_LOGO`

- Area: Player flow.
- Runtime role/status: logo transition destination; verified production
  reachable.
- Important controllers: `PROCESS_LOGO`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `PLACE_MENU`

- Area: Player flow.
- Runtime role/status: title/menu runtime destination; verified production
  reachable.
- Important controllers: `DEVICE_MENU`, `obj_loadscreen`.
- Incoming transitions: runtime dispatch; runtime variable dispatch to
  PLACE_MENU.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_alphysalley`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_alphysalley_event`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_facing`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_alphysclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_alphysdesk`, `obj_classscene`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_facing`, `obj_overworldc`, `obj_readable_room1`,
  `obj_schooldesk`, `obj_solidblock`, `obj_tem_school`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_battletest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `none placed or creation-code-created`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_beach`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_npc_room`, `obj_npc_sign`, `obj_onion_event`, `obj_overworldc`,
  `obj_solidblock`, `obj_wave_fx`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_castle_darkdoor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkdoorevent`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_castle_tutorial
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_castle_front`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_torch`, `obj_darkcastle_event`,
  `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_castle_town resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_castle_outskirts`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darklanding`, `obj_doorA`,
  `obj_mainchara`, `obj_markerB`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_castle_town resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_castle_town`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_castle_house`, `obj_castle_torch`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorX`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerX`, `obj_musicer_darkcastle`,
  `obj_npc_susiedark`, `obj_ralsei_runevent`, `obj_readable_room1`,
  `obj_savepoint`, `obj_soliddark`, `obj_sul`, `obj_sur_dark`.
- Incoming transitions: enabled placed obj_doorA from room_castle_outskirts
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_castle_front resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_castle_tutorial`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorX`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_soliddark`,
  `obj_tutorialbattleevent`.
- Incoming transitions: enabled placed obj_doorB from room_castle_darkdoor
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_1f`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_castle_torch`, `obj_cc_event`, `obj_chaseenemy`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorC`,
  `obj_doorw_musfade`, `obj_doorX_musfade`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerD`, `obj_markerw`, `obj_markerX`,
  `obj_readable_room1`, `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_entrance resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_cc_rudinn resolves room_goto_previous via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_torch`, `obj_cc_event`,
  `obj_darkcontroller`, `obj_darkponman_ow`, `obj_doorA`, `obj_doorC`,
  `obj_doorD`, `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_markerD`,
  `obj_readable_room1`, `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorB from room_cc_rurus1 resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_3f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorC`, `obj_doorD`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerD`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_cc_hathy resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_4f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bluhpainting`, `obj_castle_torch`, `obj_cc_event`,
  `obj_dancer_gen`, `obj_darkcontroller`, `obj_doorA`, `obj_doorC_musfade`,
  `obj_doorD`, `obj_doorE`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerD`, `obj_markerF`, `obj_scissordancer`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_cc_rurus2 resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_5f`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_castle_torch`, `obj_cc_event`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorC`, `obj_doorF`,
  `obj_doorw_musfade`, `obj_doorX_musfade`, `obj_mainchara`, `obj_markerB`,
  `obj_markerD`, `obj_markerE`, `obj_markerw`, `obj_markerX`, `obj_savepoint`,
  `obj_solidblock`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_cc_lancer resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_6f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorD`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_rurus_checker_event`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_cc_throneroom
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_clover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cc_event`, `obj_darkcontroller`,
  `obj_doorD_musfade`, `obj_mainchara`, `obj_markerC`, `obj_npc_room`,
  `obj_npc_room_animated`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: placed obj_doorD_musfade and Card Castle event
  controller in ordered ordered room route route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_elevator`

- Area: Area not established.
- Runtime role/status: Elevator travel and floor-selection staging driven by its
  placed elevator controller; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorw_musfade`,
  `obj_elevatorcontroller`, `obj_mainchara`, `obj_markerw`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_entrance`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorw_musfade`,
  `obj_mainchara`, `obj_markerB`, `obj_markerw`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_cc_1f resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_darkfountain`, `obj_fountainkris`.
- Incoming transitions: runtime controller and obj_event_room flow stage the
  Chapter 1 fountain presentation.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_hathy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_room`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_3f resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_joker`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; conditional.
- Important controllers: `obj_darkcontroller`, `obj_doorB`,
  `obj_jokerbattleevent`, `obj_jokerbg_triangle_real`, `obj_mainchara`,
  `obj_markerA`.
- Incoming transitions: Jevil secret-encounter room; immediately follows
  room_cc_prison_prejoker in scr_get_room_by_id, and obj_jokerbattleevent
  returns explicitly to room_cc_prison_prejoker at con == 37.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: checks global.flag\[241\] >= 6; its Step event records battle
  outcomes in flags 241 and 242.

### Chapter 1: `room_cc_kingbattle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_kingcutscene`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_npc_facing`, `obj_npc_room`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_preroof resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_lancer`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bluhpainting`, `obj_darkcontroller`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_5f resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_prefountain`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorB`,
  `obj_event_room`, `obj_mainchara`, `obj_markerA`, `obj_soliddark`.
- Incoming transitions: obj_event_room Step context runtime controller stages
  the prefountain-to-fountain flow.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_preroof`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_torch`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_npc_room`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_throneroom
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_cc_kingbattle resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_prison_cells`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorX`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_npc_room`, `obj_npc_sign`,
  `obj_prisonevent`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_cc_prisonlancer
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_prison_prejoker`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_castle_torch`, `obj_darkcontroller`,
  `obj_doorX_musfade`, `obj_event_room`, `obj_mainchara`, `obj_markerB`,
  `obj_markerX`, `obj_savepoint`, `obj_sdl_dark`, `obj_soliddark`,
  `obj_sur_dark`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorB from room_cc_joker resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_prison_to_elevator`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_cc_event`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorX_musfade`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerX`, `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_prisonlancer
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_cc_prison2 resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_prison2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_room`, `obj_npc_sign`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_prison_to_elevator
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_prisonelevator`

- Area: Area not established.
- Runtime role/status: Elevator travel and floor-selection staging driven by its
  placed elevator controller; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX_musfade`,
  `obj_elevatorcontroller`, `obj_mainchara`, `obj_markerX`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_prisonlancer`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cc_event`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorX`, `obj_lancerbattle2_event`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerX`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_prison_cells
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_cc_prison_to_elevator resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_rudinn`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_room`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_1f resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_rurus1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_rurus_event`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_cc_2f resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_rurus2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_rurus_event`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_cc_4f resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_cc_throneroom`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB_musfade`,
  `obj_event_room`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_npc_facing`, `obj_npc_room`, `obj_npc_room_animated`, `obj_npc_sign`,
  `obj_readable_room1`, `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_cc_6f resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_cc_preroof resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_chapter_continue`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chapter_continue`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark_chase1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_backgrounder_standard`, `obj_darkcontroller`,
  `obj_darkslide`, `obj_doorA`, `obj_doorB`, `obj_lancerchaseevent`,
  `obj_mainchara`, `obj_markerA`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dark7 resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark_chase2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_lancerslideevent`,
  `obj_mainchara`, `obj_markerA`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dark_chase1 resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark_eyepuzzle`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkeyepuzzle`,
  `obj_darkeyepuzzle_switch`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_musicer_darkcliff`, `obj_readable_room1`,
  `obj_savepoint`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_dark_wobbles resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_dark7 resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark_wobbles`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorD`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_soliddark`,
  `obj_wobblything_evil`.
- Incoming transitions: enabled placed obj_doorB from room_dark_eyepuzzle
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkwakeevent`, `obj_doorA`,
  `obj_mainchara`, `obj_markerB`, `obj_npc_room_animated`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dark1a resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark1a`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_savepoint`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dark1 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_dark2 resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darklancer`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_darkcliff`, `obj_readable_room1`, `obj_soliddark`,
  `obj_wobblything`.
- Incoming transitions: enabled placed obj_doorA from room_dark1a resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_dark3 resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darklancer`,
  `obj_darkslide`, `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_dustpile`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerD`,
  `obj_musicer_darkcliff`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dark2 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_dark3a resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark3a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_dustpile`,
  `obj_mainchara`, `obj_markerA`, `obj_readable_room1`, `obj_soliddark`,
  `obj_wobblything`.
- Incoming transitions: enabled placed obj_doorA from room_dark3 resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_dark7`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkslide`, `obj_doorA`,
  `obj_doorB`, `obj_dustpile`, `obj_dustpile_susie`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_readable_room1`, `obj_soliddark`,
  `obj_wobblything`.
- Incoming transitions: enabled placed obj_doorA from room_dark_eyepuzzle
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dark_chase1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_DARKempty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 1: `room_diner`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_room`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sur`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_ed`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_credits`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_empty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 1: `room_field_boxpuzzle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktile`, `obj_boxpuzzle_event`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_purplegrass`, `obj_pushableblock`,
  `obj_readable_room1`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_field3 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_field4 resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkers1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_backgrounder_standard`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_darkcliff`, `obj_ob_gen`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkers3
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_checkers5 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkers2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_backgrounder_standard`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_darkcliff`, `obj_ponman_appear`, `obj_sdl`, `obj_sdr`,
  `obj_soliddark`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkers4
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_checkers6 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkers3`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_lancerscare2`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkers6
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_checkers1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkers4`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_backgrounder_standard`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorD_musfade`, `obj_mainchara`, `obj_markerB`,
  `obj_markerC`, `obj_musicer_darkcliff`, `obj_ob_checkertile`, `obj_ob_gen`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_field_checkers2
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkers5`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_backgrounder_standard`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_darkcliff`, `obj_ponman_appear`, `obj_sdl`, `obj_sdr`,
  `obj_soliddark`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkers1
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_checkers7 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkers6`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_backgrounder_standard`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_darkcliff`, `obj_ob_checkertile`, `obj_ob_gen`, `obj_sdr`,
  `obj_soliddark`, `obj_sul`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkers2
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_checkers3 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkers7`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_npc_room`,
  `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkers5
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_checkersboss resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_checkersboss`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_backgrounder_standard`, `obj_checker_animtest`,
  `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_musicer_darkcliff`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkers7
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_savepoint1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_forest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_musicer_bird`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_start resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_field1 resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_getsusie`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_getsusieevent`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_musicer_field`,
  `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_field_puzzle2
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_shop1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_maze`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_hathyfightevent`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_field`, `obj_npc_room`, `obj_npc_room_animated`, `obj_npc_sign`,
  `obj_purplegrass`, `obj_savepoint`, `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_field_puzzle1
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_puzzle2 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_puzzle1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_event_room`, `obj_glowtile`, `obj_glowtilepuzz`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_npc_room`,
  `obj_purplegrass`, `obj_readable_room1`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_field_topchef
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_maze resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_puzzle2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_glowtile`, `obj_glowtilepuzz`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_musicer_field`, `obj_purplegrass`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_maze resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_field_getsusie resolves room_goto_previous via scr_get_room_by_id
  asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_puzzletutorial`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_musicer_field`, `obj_npc_puzzlemaster2`, `obj_npc_room`,
  `obj_npc_sign`, `obj_purplegrass`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_shop1 resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_secret1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorB`,
  `obj_event_room`, `obj_mainchara`, `obj_markerA`, `obj_npc_sign`,
  `obj_purplegrass`, `obj_soliddark`, `obj_solidenemy`, `obj_suitspuzz_button`,
  `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_field4 resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_shop1`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_doorX_musfade`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_markerX`,
  `obj_musicer_field`, `obj_npc_puzzlemaster1`, `obj_purplegrass`,
  `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_field_puzzletutorial
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_start`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_musicer_bird`, `obj_savepoint`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_field_forest resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field_topchef`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorD`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_npc_room`,
  `obj_purplegrass`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_field_puzzle1
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB_musfade`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_field`, `obj_npc_sign`, `obj_purplegrass`, `obj_soliddark`,
  `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_field_forest resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_field2 resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorC`, `obj_event_room`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerD`, `obj_npc_facing`, `obj_npc_sign`,
  `obj_purplegrass`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_field1 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_field2A resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field2A`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_event_room`,
  `obj_mainchara`, `obj_markerA`, `obj_npc_room`, `obj_npc_sign`,
  `obj_purplegrass`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field2 resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorD`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_markerw`,
  `obj_musicer_field`, `obj_purplegrass`, `obj_scarelancerevent`,
  `obj_shortcut_door`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_field_boxpuzzle
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_field4`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorC_musfade`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerD`, `obj_musicer_field`, `obj_purplegrass`,
  `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_field_boxpuzzle
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_field_secret1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_flowershop_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorX`, `obj_flowershop_event`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sul`, `obj_sur`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_flowershop_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_flowershop_event`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_sign`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_afterthrash2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerX`,
  `obj_musicer_bird`, `obj_soliddark`, `obj_thrashafter_follow`.
- Incoming transitions: enabled placed obj_doorB from room_forest_afterthrash3
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_afterthrash3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`,
  `obj_thrashafter_follow`.
- Incoming transitions: enabled placed obj_doorA from room_forest_afterthrash2
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_afterthrash4 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_afterthrash4`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`,
  `obj_thrashafter_follow`.
- Incoming transitions: enabled placed obj_doorA from room_forest_afterthrash3
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_castleview resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area0`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB_musfade`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_musicer_forest`,
  `obj_rabbick_bush`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_forest_savepoint1
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_area1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_musicer_forest`,
  `obj_npc_facing`, `obj_npc_room`, `obj_rabbick_bush`, `obj_readable_room1`,
  `obj_soliddark`, `obj_solidenemy`, `obj_susiebadguy_event`.
- Incoming transitions: enabled placed obj_doorA from room_forest_area0 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_forest_area2 resolves room_goto_previous via scr_get_room_by_id
  asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkponman_ow`, `obj_doorA`,
  `obj_doorB`, `obj_doorC`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerD`, `obj_musicer_forest`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_area1 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_forest_area2A resolves room_goto_previous via scr_get_room_by_id
  asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area2A`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_room`, `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_forest_area2 resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cloverhole`, `obj_cloverpuzzle_event`,
  `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorD`, `obj_mainchara`,
  `obj_markerB`, `obj_markerC`, `obj_musicer_forest`, `obj_readable_room1`,
  `obj_soliddark`, `obj_suitspuzz_button`.
- Incoming transitions: enabled placed obj_doorB from room_forest_savepoint2
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area3A`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_room`, `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_forest_beforeclover
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area4`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_chaseenemy`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorD_musfade`, `obj_mainchara`,
  `obj_markerB`, `obj_markerC`, `obj_markerX`, `obj_musicer_forest`,
  `obj_npc_room`, `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorB from room_forest_dancers1
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_area5`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_darkcontroller`,
  `obj_darkponman_ow`, `obj_doorA`, `obj_doorX_musfade`,
  `obj_forest_area5_puzzle`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_readable_room1`, `obj_soliddark`, `obj_tempblock_room`.
- Incoming transitions: enabled placed obj_doorA from room_forest_starwalker
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_savepoint_relax resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_beforeclover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorC`, `obj_event_room`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerD`, `obj_soliddark`, `obj_suitspuzz_button`.
- Incoming transitions: enabled placed obj_doorA from room_forest_puzzle1
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_area3A resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_castlefront`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castlefront_event`, `obj_darkcontroller`,
  `obj_doorw_musfade`, `obj_doorX`, `obj_mainchara`, `obj_markerA`,
  `obj_markerw`, `obj_markerX`, `obj_purplegrass`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_chase2
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_castleview`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`,
  `obj_thrashafter_follow`.
- Incoming transitions: enabled placed obj_doorA from room_forest_afterthrash4
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_chase1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_lancerchase2`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_purplegrass`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_castleview
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_chase2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_lancerchase2`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerX`,
  `obj_overworld_spademaker`, `obj_purplegrass`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_chase1
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_dancers1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_dancer_gen`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorC`, `obj_doorX`, `obj_lightfairy`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_markerX`,
  `obj_musicer_forest`, `obj_soliddark`, `obj_solidenemy`, `obj_solidenemy_2`,
  `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_forest_area4 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_forest_secret1 resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_fightsusie`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB_musfade`, `obj_doorX`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_bird`, `obj_npc_room`, `obj_shortcut_door`, `obj_soliddark`,
  `obj_susieandlancer_event`.
- Incoming transitions: enabled placed obj_doorA from room_forest_savepoint3
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_afterthrash2 resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_maze_deadend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_facing`, `obj_soliddark`.
- Incoming transitions: runtime variable dispatch to room_forest_maze_deadend.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_maze_deadend2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorD`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_facing`, `obj_soliddark`.
- Incoming transitions: runtime variable dispatch to room_forest_maze_deadend2.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_maze_susie`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_event_room`,
  `obj_mainchara`, `obj_markerA`, `obj_markerD`, `obj_markerX`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime variable dispatch to
  room_forest_maze_susie.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_maze1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_battlealphaer`, `obj_darkcontroller`, `obj_doorX`,
  `obj_forestmaze_controller`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerX`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorB from room_forest_maze_deadend
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch; runtime variable dispatch to room_forest_maze1.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_maze2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_battlealphaer`, `obj_darkcontroller`, `obj_doorX`,
  `obj_forestmaze_controller`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerX`, `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: runtime dispatch; runtime variable dispatch to
  room_forest_maze2.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_puzzle1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorD`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_npc_sign`,
  `obj_soliddark`, `obj_suitspuzz_button`, `obj_suitspuzzle_event`.
- Incoming transitions: enabled placed obj_doorB from room_forest_beforeclover
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_savepoint_relax`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_doorX`,
  `obj_event_room`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerX`, `obj_musicer_forest`, `obj_npc_room`, `obj_npc_room_animated`,
  `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_area5 resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_savepoint1`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA_musfade`,
  `obj_doorB_musfade`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerw`, `obj_musicer_quietforest`, `obj_npc_room`, `obj_savepoint`,
  `obj_shortcut_door`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_field_checkersboss
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_forest_area0 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_savepoint2`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_doorC_musfade`, `obj_lancerbakesale_event`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_quietforest`, `obj_npc_room`, `obj_savepoint`,
  `obj_shortcut_door`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_area3 resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_forest_smith resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_savepoint3`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorX`,
  `obj_event_room`, `obj_mainchara`, `obj_markerB`, `obj_markerX`,
  `obj_musicer_forest`, `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_forest_fightsusie
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch; runtime dispatch; runtime variable dispatch to
  room_forest_savepoint3.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_secret1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorB`,
  `obj_doorX`, `obj_mainchara`, `obj_markerA`, `obj_markerX`, `obj_soliddark`,
  `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_forest_dancers1
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_smith`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_hammerguy`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_savepoint2
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_starwalker`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_battlealphaer`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerX`,
  `obj_musicer_forest`, `obj_sdl_dark`, `obj_sdr`, `obj_soliddark`,
  `obj_starwalker_offswitch`, `obj_starwalker_overworld`, `obj_sul`, `obj_sur`,
  `obj_sur_dark`.
- Incoming transitions: enabled placed obj_doorA from room_forest_thrashmaker
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_forest_thrashmaker`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorD`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_readable_room1`,
  `obj_soliddark`, `obj_thrashmaker_event`.
- Incoming transitions: enabled placed obj_doorB from room_forest_starwalker
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_gameover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_gameover_init`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_graveyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_markerX`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_sur`, `obj_town_event`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_hospital_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_hospital_lobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorW`, `obj_mainchara`,
  `obj_markerB`, `obj_markerw`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_hospital_room2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_hospital_rudy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_overworldc`, `obj_readable_room1`, `obj_rudy`, `obj_solidblock`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `ROOM_INITIALIZE`

- Area: Bootstrap.
- Runtime role/status: runtime initialization room; bootstrap.
- Important controllers: `obj_debugcontroller`, `obj_gamecontroller`,
  `obj_initializer2`, `obj_roomcontroller`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 1: `room_insidecloset`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_fallpaper`, `obj_insideclosetcutscene`,
  `obj_mainchara`, `obj_overworldc`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_krishallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_doorC`, `obj_event_room`,
  `obj_hallway_mirror`, `obj_mainchara`, `obj_markerA`, `obj_markerD`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_krisroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_krisroom`, `obj_mainchara`,
  `obj_markerB`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_legend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_legend`.
- Incoming transitions: runtime dispatch; runtime variable dispatch to
  room_legend.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_library`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_facing`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_man`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_darkcontroller`,
  `obj_doorX_musfade`, `obj_mainchara`, `obj_markerX`, `obj_musicer_man`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_myroom_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_dkris_event`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_school_unusedroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_unusedclassevent`.
- Incoming transitions: non-production unused classroom; excluded from ordered
  adjacency and only referenced by unused/fountain cleanup/readable-room
  compatibility code.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_schooldoor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkdoor`, `obj_doorC`, `obj_doorD`,
  `obj_mainchara`, `obj_markerC`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_schoollobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorB`, `obj_doorC`,
  `obj_doorX_musfade`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerD`, `obj_markerX`, `obj_overworldc`, `obj_readable_room1`,
  `obj_schoollobbycutscene`, `obj_solidblock`, `obj_sul`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_shop1`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop1`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_shop2`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop2`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_splashscreen`

- Area: Startup presentation.
- Runtime role/status: startup splash presentation driven by obj_splashscreen;
  verified production reachable.
- Important controllers: `obj_splashscreen`.
- Incoming transitions: startup presentation driven by sole placed
  obj_splashscreen controller.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_torbathroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_sur`, `obj_town_event`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_torhouse`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorD`, `obj_doorX_musfade`,
  `obj_event_room`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerX`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdl`, `obj_sdr`, `obj_solidblock`, `obj_solidlong`, `obj_sul`, `obj_sur`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_torielclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_mainchara`,
  `obj_markerB`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_torielclass_event`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_torroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_apartments`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_church`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_event`, `obj_doorA`, `obj_doorC_musfade`,
  `obj_doorD`, `obj_doorX`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerD`, `obj_markerX`, `obj_musicer_town`, `obj_npc_room`,
  `obj_overworldc`, `obj_sdl`, `obj_sdr`, `obj_solidblock`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_krisyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_carcutscene`, `obj_doorC`, `obj_doorX_musfade`,
  `obj_event_room`, `obj_mainchara`, `obj_markerD`, `obj_markerX`,
  `obj_musicer_town`, `obj_npc_sign`, `obj_overworldc`, `obj_sdl`, `obj_sdr`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_mid`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorC`, `obj_doorD`,
  `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markerC`, `obj_markerD`,
  `obj_markerw`, `obj_markerX`, `obj_npc_facing`, `obj_npc_room`,
  `obj_npc_room_animated`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_town_event`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_north`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorC`, `obj_doorD`, `obj_doorX`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_markerD`, `obj_markerX`,
  `obj_npc_facing`, `obj_npc_room`, `obj_npc_sign`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_northwest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_school`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_doorX_musfade`, `obj_mainchara`,
  `obj_markerA`, `obj_markerX`, `obj_musicer_town`, `obj_overworldc`, `obj_sdr`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_shelter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorD_musfade`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_sdl`, `obj_sdr`,
  `obj_solidblock`, `obj_sul`, `obj_sur`, `obj_town_shelter_event`.
- Incoming transitions: ordered Light World ordered route and placed
  door/overworld-controller route in ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_town_south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_doorC`,
  `obj_doorD`, `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markerB`,
  `obj_markerC`, `obj_markerD`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_town`, `obj_npc_facing`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sul`, `obj_town_event`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 1: `room_townhall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_sdl`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

## Chapter 2 (278 assets)

### Chapter 2: `PLACE_CONTACT`

- Area: Player flow.
- Runtime role/status: contact or chapter-entry runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_CONTACT_old`.
- Incoming transitions: runtime dispatch; runtime variable dispatch to
  PLACE_CONTACT.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `PLACE_DOG`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `PROCESS_DOG`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 2: `PLACE_DOGCHECK2`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_dogcheck2`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 2: `PLACE_FAILURE`

- Area: Player flow.
- Runtime role/status: failure/game-over runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_FAILURE`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `PLACE_LOGO`

- Area: Player flow.
- Runtime role/status: logo transition destination; verified production
  reachable.
- Important controllers: `PROCESS_LOGO`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `PLACE_MENU`

- Area: Player flow.
- Runtime role/status: title/menu runtime destination; verified production
  reachable.
- Important controllers: `DEVICE_MENU`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `PLACE_NAMING_JIKKEN`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `DEVICE_NAMER`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 2: `room_alphysalley`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorW`, `obj_mainchara`, `obj_markerw`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_alphysclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_alphysdesk`, `obj_classscene`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_facing`, `obj_overworldc`, `obj_readable_room1`,
  `obj_schooldesk`, `obj_solidblock`, `obj_tem_school`.
- Incoming transitions: enabled placed obj_doorA from room_schoollobby resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_battletest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_battletester`, `obj_chaseenemy`,
  `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 2: `room_beach`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_beach`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_room`, `obj_npc_sign`, `obj_onion_event`,
  `obj_overworldc`, `obj_solidblock`, `obj_wave_fx`.
- Incoming transitions: enabled placed obj_doorA from room_town_north resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_bullettest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_bullettester`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 2: `room_castle_town`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_castle_house`, `obj_castle_torch`,
  `obj_ch2_scene4`, `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorD`,
  `obj_doorX`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerC`,
  `obj_markerX`, `obj_musicer_darkcastle`, `obj_npc_susiedark`,
  `obj_readable_room1`, `obj_savepoint`, `obj_soliddark`, `obj_sul`,
  `obj_sur_dark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_castle_tutorial`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_castle_tutorial`, `obj_darkcontroller`,
  `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markers`, `obj_markerw`,
  `obj_markerX`, `obj_musicer_darkcastle`, `obj_npc_room`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_castle_town resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch; runtime
  dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_cc_clover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorD_musfade`,
  `obj_mainchara`, `obj_markerC`, `obj_npc_room`, `obj_npc_room_animated`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_cc_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_darkfountain`, `obj_fountainkris`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_cc_lancer`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bluhpainting`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_markerX`, `obj_npc_room`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_chapter_continue`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chapter_continue`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_cutscene_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_conveyorbelt`, `obj_cutscene_test`,
  `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorAny`, `obj_forcefield`,
  `obj_mainchara`, `obj_npc_sign`, `obj_soliddark`, `obj_sticky_example`,
  `obj_swordobj_example`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_krishallway.
- Conditions: No additional condition verified.

### Chapter 2: `room_cutscene_tester_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_example_cutscene_b`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_DARKbase_GMS2`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 2: `room_DARKempty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 2: `room_debug_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_battle`, `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_debug_battleBalloon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_ballooner`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_debug_choicer_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_choicer`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_debug_choicer_light`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_choicer`, `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_debug_color`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_swatchling`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_debug_loc`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_loc`, `obj_hallway_mirror`, `obj_mainchara`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_solidlong`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_debug_smallface`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_smallfacetester`, `obj_mainchara`,
  `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_debug_smallface_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_smallfacetester`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_diner`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_town_diner`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_catti`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sur`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_area_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_castle_area_1`, `obj_darkcontroller`,
  `obj_doorX`, `obj_dw_leave`, `obj_mainchara`, `obj_markerB`, `obj_markerX`,
  `obj_sdl_dark`, `obj_sdr_dark`, `obj_soliddark`, `obj_sul_dark`,
  `obj_sur_dark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_castle_area_2
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_area_2`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_castle_house`, `obj_castle_torch`,
  `obj_ch2_scene4`, `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorD`,
  `obj_doorX`, `obj_mainchara`, `obj_markerB`, `obj_markerr`, `obj_markerw`,
  `obj_markerX`, `obj_musicer_darkcastle`, `obj_readable_room1`,
  `obj_savepoint`, `obj_soliddark`, `obj_sul`, `obj_sur_dark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_area_2_transformed`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_castle_cafe`,
  `obj_castle_dojo`, `obj_castle_house`, `obj_castle_restaurant`,
  `obj_castle_shop`, `obj_castle_torch`, `obj_ch2_room_castle_transformed`,
  `obj_ch2_scene6`, `obj_darkcontroller`, `obj_doorA`, `obj_doorX`,
  `obj_doorX_musfade`, `obj_mainchara`, `obj_markerB`, `obj_markerr`,
  `obj_markers`, `obj_markert`, `obj_markeru`, `obj_markerv`, `obj_markerw`,
  `obj_markerX`, `obj_musicer_darkcastle`, `obj_npc_room`, `obj_readable_room1`,
  `obj_savepoint`, `obj_sdl_dark`, `obj_sdr_dark`, `obj_soliddark`, `obj_sul`,
  `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_castle_area_2
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_ralsei_castle_front resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_cafe`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_cafe`, `obj_npc_castle_cafe`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_dojo`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_dojo_allstarsPlaylist`,
  `obj_ch2_room_castle_dojo`, `obj_darkcontroller`, `obj_dojofx`, `obj_doorX`,
  `obj_mainchara`, `obj_markerX`, `obj_readable_room1`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_dungeon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_dungeon_2f`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerw`, `obj_npc_king`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_east_door`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_castle_door`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_restaurant`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_castle_bakery`, `obj_sdl`, `obj_sdr`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_rooms_hallway`

- Area: Castle Town.
- Runtime role/status: Castle residential hallway connecting character rooms;
  verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: placed obj_mainchara; Castle rooms controller dispatch
  context runtime controller.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_rooms_kris`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_castle_kris`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerv`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_rooms_lancer`

- Area: Castle Town.
- Runtime role/status: Lancer room interior reached from the residential
  hallway; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: placed obj_mainchara; Castle rooms controller dispatch
  context runtime controller.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_rooms_susie`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_castle_susie`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerw`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_west_cliff`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darklanding`, `obj_doorX`,
  `obj_mainchara`, `obj_markerD`, `obj_markerX`, `obj_npc_castle_cliff`,
  `obj_npc_room`, `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_castle_west_cliff_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darklanding`, `obj_doorX`,
  `obj_mainchara`, `obj_markerX`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_baseball`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch2_city07`,
  `obj_cybercity_balloon`, `obj_cybercity_bg_screen`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_city`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_monologue
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_postbaseball_1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_berdly`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city_berdly`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_doorB_musfade`, `obj_doorW`, `obj_mainchara`,
  `obj_markerA`, `obj_markerv`, `obj_markerX`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: door from room_dw_city_poppup; enabled placed obj_doorA
  from room_dw_city_poppup resolves room_goto_next via scr_get_room_by_id asset
  order; runtime dispatch.
- Outgoing transitions: to room_dw_city_poppup.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_big_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_tutorialViroMaker`, `obj_chaseenemy`,
  `obj_cybercity_bg_lightset`, `obj_cybercity_bg_screen`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerAny`, `obj_markerB`,
  `obj_markerw`, `obj_markerX`, `obj_musicer_city`, `obj_npc_room`,
  `obj_solidblocksized`, `obj_solidenemy`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_mice resolves
  room_goto_next via scr_get_room_by_id asset order; enabled placed obj_doorB
  from room_dw_city_traffic_2 resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_big_1_original`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerw`, `obj_markerX`, `obj_npc_room`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_big_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_alleySwitch`, `obj_bg_givedepth`,
  `obj_chaseenemy`, `obj_city_parallaxStreet`, `obj_cone`,
  `obj_controller_dw_city_big_2`, `obj_cybercity_bg_lightset`,
  `obj_cybercity_bg_screen`, `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerX`,
  `obj_musicer_city`, `obj_npc_room`, `obj_readable_room1`,
  `obj_solidblocksized`, `obj_solidenemy`, `obj_triggervolume`,
  `obj_weirdEvent_addison_city_big_2`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_traffic_2
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_queen_drunk resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[915\] > 2); if (global.flag\[915\] == 3 &&
  global.flag\[916\] == 0).

### Chapter 2: `room_dw_city_big_2_OG`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerX`, `obj_npc_room`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_big_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_cone`,
  `obj_cybercity_bg_carbridge`, `obj_cybercity_bg_lightset`,
  `obj_cybercity_bg_screen`, `obj_cybercity_bg_sign`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB_musfade`, `obj_mainchara`, `obj_markerAny`, `obj_markerB`,
  `obj_musicer_city`, `obj_npc_addison_tea`, `obj_npc_room`, `obj_npc_sign`,
  `obj_solidblocksized`, `obj_solidenemy`, `obj_sprite_part_parallax_example`,
  `obj_sprite_part_parallax_inverted`, `obj_treasure_room`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_savepoint
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_traffic_3 resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_big_3_backup_2exits`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_cone`,
  `obj_cybercity_bg_carbridge`, `obj_cybercity_bg_lightset`,
  `obj_cybercity_bg_screen`, `obj_cybercity_bg_sign`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB_musfade`, `obj_doorW`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerw`, `obj_musicer_city`, `obj_npc_addison_tea`,
  `obj_npc_room`, `obj_npc_sign`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_sprite_part_parallax_example`, `obj_sprite_part_parallax_inverted`,
  `obj_treasure_room`, `obj_weirdroute_manipulator`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_big_3_og`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerw`, `obj_npc_addison_tea`, `obj_npc_room`, `obj_npc_sign`,
  `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_carnival`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_mazecheese`,
  `obj_npc_room`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_cheese
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_cheese`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_npc_city_cheese`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_city_traffic_3_2Entrances resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_city_carnival resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_cheesemaze`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_city_cheesemaze`,
  `obj_cybercity_bg_sign`, `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_mazecheese`,
  `obj_musicer_city`, `obj_solidblock_destructable`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_treasure_room`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_mice2
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_mice3 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_dog_traffic`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dogcar_controller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerX`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_entrance`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_city_parallaxStreet`, `obj_cityEntrance_event`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB_musfade`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_musicer_city`, `obj_savepoint`,
  `obj_solidblocksized`, `obj_sprite_part_parallax_example`,
  `obj_sprite_part_parallax_inverted`, `obj_weirdroute_manipulator`,
  `obj_welcometothecity_backinglights`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_split
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_traffic_1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_hacker`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city01`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_city`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_roadblock
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_mice resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_intro`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch2_scene11b`,
  `obj_city_trashbag`, `obj_cybercity_trashcan`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerw`, `obj_musicer_room`, `obj_shortcut_door`, `obj_solidblocksized`,
  `obj_soliddark`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_spamton_house
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_split resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_man`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_ch2_room_city_man`,
  `obj_darkcontroller`, `obj_doorw_musfade`, `obj_mainchara`, `obj_markerX`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_mansion_front`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city08`, `obj_darkcontroller`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerX`, `obj_queenmansion_bg`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: door from room_dw_city_poppup.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_mice`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_controller_dw_city_mice`,
  `obj_cybercity_mousesign`, `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_holemouse_block_clockwise_moveable`, `obj_holemouse_generator`,
  `obj_holemouse_goal`, `obj_holemouse_invis_clockwise`, `obj_mainchara`,
  `obj_markerAny`, `obj_mouseSpawnSwitch`, `obj_musicer_city`, `obj_npc_sign`,
  `obj_readable_room1`, `obj_resetBell`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_hacker
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_big_1 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.plot < 72); if (global.plot >= 72); if (global.plot >=
  72).

### Chapter 2: `room_dw_city_mice2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_camera_area`, `obj_controller_city_mice2`,
  `obj_cybercity_bg_sign`, `obj_cybercity_mousesign`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_forcefield`, `obj_holemouse_generator`,
  `obj_holemouse_goal`, `obj_holemouse_invis_clockwise`,
  `obj_holemouse_invis_counterclockwise`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_mice2Switch`, `obj_musicer_city`, `obj_npc_sign`,
  `obj_readable_room1`, `obj_rotationController_track`,
  `obj_rotationTile_track1`, `obj_rotationTile_track2`,
  `obj_rotationTile_track3`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_traffic_3
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_cheesemaze resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[368\] == 0 || (global.flag\[915\] != 0 &&
  global.flag\[916\] == 0)); if (global.flag\[368\] == 0 || (global.flag\[915\]
  != 0 && global.flag\[916\] == 0)); if (global.flag\[368\] == 0 ||
  (global.flag\[915\] != 0 && global.flag\[916\] == 0)); if (global.flag\[368\]
  == 1); if (global.plot >= 120); if ((global.flag\[915\] != 0 &&
  global.flag\[916\] == 0) || global.plot < 120); if (global.flag\[368\] == 1);
  if (global.flag\[368\] == 0 || (global.flag\[915\] != 0 && global.flag\[916\]
  == 0)); if (global.flag\[368\] == 0 || (global.flag\[915\] != 0 &&
  global.flag\[916\] == 0)); if (global.flag\[368\] == 0 || (global.flag\[915\]
  != 0 && global.flag\[916\] == 0)); if (global.flag\[368\] == 0 ||
  (global.flag\[915\] != 0 && global.flag\[916\] == 0)).

### Chapter 2: `room_dw_city_mice2_og`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_forcefield`,
  `obj_holemouse_block_clockwise`, `obj_holemouse_block_counterclockwise`,
  `obj_holemouse_generator`, `obj_holemouse_goal`,
  `obj_holemouse_invis_clockwise`, `obj_holemouse_invis_counterclockwise`,
  `obj_mainchara`, `obj_markerA`, `obj_mouseTrigger`, `obj_resetBell`,
  `obj_solidblocksized`, `obj_solidenemy`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_mice3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_controller_city_mice3`, `obj_cybercity_mousesign`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_dw_city_mice3Fence`,
  `obj_forcefield`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_masterPlatformController`, `obj_mouseTowerTrigger`, `obj_musicer_city`,
  `obj_npc_sign`, `obj_solidblocksized`, `obj_trigger_area`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_cheesemaze
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_poppup resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[379\] == 1); if (global.flag\[379\] == 1); if
  (global.flag\[379\] == 0); if (global.flag\[379\] == 0); if
  (global.flag\[379\] == 0).

### Chapter 2: `room_dw_city_mirrorfriend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_ch2_room_city_susie_ralsei_fun_2`,
  `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`, `obj_markerX`,
  `obj_musicer_city`, `obj_npc_room`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[915\] == 3 && global.flag\[916\] == 0).

### Chapter 2: `room_dw_city_monologue`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city_noelle_monologue`,
  `obj_ch2_keyboardpuzzle_monologue_controller`,
  `obj_ch2_noellepuzzle_cityscape`, `obj_ch2_noellepuzzle_forcefield`,
  `obj_ch2_noellepuzzle_key_kris`, `obj_ch2_noellepuzzle_key_noelle`,
  `obj_ch2_noellepuzzle_screen`, `obj_darkcontroller`, `obj_doorA`, `obj_doorW`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_silhouette_base`,
  `obj_silhouette_cover`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_city_baseball
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_monologue_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch2_blue_button`,
  `obj_ch2_keyboardpuzzle_monologue_controller`,
  `obj_ch2_keyboardpuzzle_solo_tile`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorW`, `obj_forcefield`, `obj_mainchara`, `obj_markerB`, `obj_markerX`,
  `obj_silhouette_base`, `obj_silhouette_cover`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_moss`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_city_moss`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerX`, `obj_musicer_city`,
  `obj_readable_room1`, `obj_soliddark`, `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_noelle_fight_intro`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_carnival
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_poppup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cone`, `obj_cybercity_bg_screen_dolphin`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_cybercity_trashcan`,
  `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorAny`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerX`,
  `obj_musicer_city`, `obj_overworld_poppup`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`, `obj_weirdroute_sewerEntrance`.
- Incoming transitions: door from room_dw_city_berdly; enabled placed obj_doorA
  from room_dw_city_mice3 resolves room_goto_next via scr_get_room_by_id asset
  order; enabled placed obj_doorB from room_dw_city_berdly resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: to room_dw_city_berdly; to room_dw_city_mansion_front.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_postbaseball_1`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_bug_treasure_chest`,
  `obj_city_postbaseball_background`, `obj_cone`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_city`, `obj_npc_sign`, `obj_pushtile_room`, `obj_readable_room1`,
  `obj_room_dw_city_postbaseball`, `obj_savepoint`, `obj_sdl_dark`,
  `obj_sdr_dark`, `obj_solidblocksized`, `obj_soliddark`, `obj_solidenemy`,
  `obj_sul_dark`, `obj_sur_dark`, `obj_teacup`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_baseball
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_postbaseball_2 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_postbaseball_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_city_postbaseball_background`,
  `obj_cybercity_balloon`, `obj_cybercity_balloon_cheese`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_city`, `obj_pushtile_room`, `obj_room_dw_city_postbaseball`,
  `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_city_postbaseball_1 resolves room_goto_next via scr_get_room_by_id
  asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_postbaseball_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_city_postbaseball_background`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_city`, `obj_pushtile_room`, `obj_room_dw_city_postbaseball`,
  `obj_sdr_dark`, `obj_solidblocksized`, `obj_sul_dark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_city_postbaseball_2 resolves room_goto_next via scr_get_room_by_id
  asset order; enabled placed obj_doorB from room_dw_city_mansion_front resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_prototype_01`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_cybercity_bg_carbridge`,
  `obj_cybercity_bg_lightset`, `obj_cybercity_bg_screen`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_darkcontroller`, `obj_doorA`,
  `obj_mainchara`, `obj_markerB`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_prototype_02`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_cybercity_bg_lightset`, `obj_cybercity_bg_screen`,
  `obj_cybercity_bg_sign`, `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_queen_drunk`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene13`, `obj_darkcontroller`,
  `obj_doorA_musfade`, `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_musicer_city`, `obj_npc_sign`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_big_2
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_savepoint resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_roadblock`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city_noelle_chase`,
  `obj_ch2_tutorialViroMaker`, `obj_city_parallaxStreet`,
  `obj_cybercity_bg_sign`, `obj_cybercity_bg_trafficlight_shine`,
  `obj_cybercity_trashcan`, `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_musicer_city`,
  `obj_npc_room_animated`, `obj_overworld_poppup`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_traffic_1
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_hacker resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_savepoint`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch2_room_city_savepoint`,
  `obj_cybercity_bg_lightset`, `obj_darkcontroller`, `obj_doorA_musfade`,
  `obj_doorB_musfade`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_room`, `obj_savepoint`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_queen_drunk
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_big_3 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_sidewayscars`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_charmarker`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_traffic_car_generator`, `obj_traffic_switch`.
- Incoming transitions: placed obj_traffic_car_generator and obj_traffic_switch;
  controller contexts runtime controller and runtime controller.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_spamton_alley`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city05`, `obj_darkcontroller`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerw`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_traffic_4
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_spamton_house`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch2_room_city_spamton_house`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerB`, `obj_musicer_room`, `obj_queenscreen`,
  `obj_soliddark`, `obj_solidenemy`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_city_spamton_shop_exterior resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_city_intro resolves room_goto_previous via scr_get_room_by_id asset
  order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_spamton_shop_exterior`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`,
  `obj_ch2_room_spamton_shop_exterior`, `obj_darkcontroller`, `obj_doorA`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerB`, `obj_musicer_room`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_city_spamton_house
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_spamton_shop_interior`

- Area: Cyber City.
- Runtime role/status: decorative/interior-named asset; no dispatch to the real
  Spamton shop UI was verified; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_mainchara`,
  `obj_markerB`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_split`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene12`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_room`, `obj_overworld_poppup`, `obj_readable_room1`,
  `obj_soliddark`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_intro
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_entrance resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_susie_ralsei_fun_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_susie_ralsei_fun`, `obj_cybercity_balloon`,
  `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`, `obj_markerX`,
  `obj_musicer_city`, `obj_readable_room1`, `obj_solidblocksized`,
  `obj_sprite_part_parallax_example`, `obj_sprite_part_parallax_inverted`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_traffic_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city_noelle_chase`, `obj_charmarker`,
  `obj_city_parallaxStreet`, `obj_controller_noelleTraffic`,
  `obj_cybercity_bg_sign`, `obj_cybercity_bg_trafficlight_shine`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_musicer_city`, `obj_readable_room1`,
  `obj_roadcrossing`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_sprite_part_parallax_example`, `obj_sprite_part_parallax_inverted`,
  `obj_traffic_car_generator`, `obj_traffic_road_trigger`, `obj_traffic_switch`,
  `obj_triggervolume`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_entrance
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_roadblock resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_traffic_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_charmarker`, `obj_city_parallaxStreet`,
  `obj_controller_noelleTraffic`, `obj_cybercity_bg_sign`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_city`, `obj_npc_room`, `obj_npc_sign`, `obj_roadcrossing`,
  `obj_solidblocksized`, `obj_solidenemy`, `obj_sprite_part_parallax_example`,
  `obj_sprite_part_parallax_inverted`, `obj_traffic_car_generator`,
  `obj_traffic_road_trigger`, `obj_traffic_switch`, `obj_triggervolume`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_big_1
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_big_2 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[915\] == 3 && global.flag\[916\] == 0).

### Chapter 2: `room_dw_city_traffic_2_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_charmarker`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerw`, `obj_npc_room`, `obj_npc_sign`, `obj_soliddark`,
  `obj_traffic_car_generator`, `obj_traffic_switch`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_traffic_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_carKiller`, `obj_charmarker`, `obj_cone`,
  `obj_controller_noelleTraffic`, `obj_cybercity_bg_sign`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorw_musfade`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerX`, `obj_musicer_city`, `obj_readable_room1`,
  `obj_roadcrossing`, `obj_sdl`, `obj_sdr`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_solidenemy_2`, `obj_sul`, `obj_sur`,
  `obj_traffic_car_generator`, `obj_traffic_road_trigger`, `obj_traffic_switch`,
  `obj_triggervolume`, `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_city_big_3
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_city_mice2 resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_traffic_3_2Entrances`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_carKiller`, `obj_charmarker`, `obj_cone`,
  `obj_controller_noelleTraffic`, `obj_cybercity_bg_sign`,
  `obj_cybercity_bg_trafficlight_shine`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_doorw_musfade`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerw`, `obj_markerX`, `obj_musicer_city`,
  `obj_roadcrossing`, `obj_sdl`, `obj_sdr`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_solidenemy_2`, `obj_sul`, `obj_sur`,
  `obj_traffic_car_generator`, `obj_traffic_road_trigger`, `obj_traffic_switch`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorB from room_dw_city_cheese
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_traffic_3_backup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_charmarker`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_doorw_musfade`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_markerw`, `obj_markerX`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_traffic_car_generator`, `obj_traffic_switch`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_traffic_4`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_city_car_a`, `obj_ch2_city_car_b`,
  `obj_ch2_room_city_traffic_jam`, `obj_cone`, `obj_darkcontroller`,
  `obj_doorA_musfade`, `obj_doorW`, `obj_doorw_musfade`, `obj_mainchara`,
  `obj_markerB`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_city`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_city_spamton_alley
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_traffic_5_old`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging;
  uncertain-no-ingress.
- Important controllers: `obj_ch2_city04`, `obj_charmarker`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_savepoint`, `obj_soliddark`,
  `obj_traffic_car_generator`, `obj_traffic_switch`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_city_treasure`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_musicer_city`, `obj_readable_room1`, `obj_soliddark`,
  `obj_treasure_room`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_battle_maze_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cyber_tree_spin`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_dw_cyber_battle_maze_controller`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_musicer_cyber`, `obj_parallaxer_cyber_2`,
  `obj_queenscreen`, `obj_queenscreen_large`, `obj_solidblocksized`,
  `obj_teacup`, `obj_teacup_landingspot`, `obj_teacup_reverser`,
  `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_savepoint
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_cyber_music_bullet resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_battle_maze_1_Original`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markeru`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_battle_maze_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_checkmarktreasurebox`, `obj_cyber_light`,
  `obj_cyber_tree_spin`, `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`,
  `obj_cyber_wall_lights_right`, `obj_darkcontroller`, `obj_doorA_musfade`,
  `obj_doorD`, `obj_doorW`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerw`, `obj_musicer_cyber`, `obj_npc_room`, `obj_solidblocksized`,
  `obj_teacup`, `obj_teacup_landingspot`, `obj_teacup_reverser`.
- Incoming transitions: enabled placed obj_doorB from room_dw_cyber_music_final
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.plot >= 60); if (global.plot >= 60).

### Chapter 2: `room_dw_cyber_battle_maze_2_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_checkmarktreasurebox`,
  `obj_controller_dw_cyber_battle_maze_2`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorD`, `obj_doorW`, `obj_forcefield`, `obj_mainchara`, `obj_markerB`,
  `obj_markerC`, `obj_markerw`, `obj_solidblock`, `obj_teacup`,
  `obj_teacup_landingspot`, `obj_teacup_reverser`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[332\] == 1).

### Chapter 2: `room_dw_cyber_battle_maze_2_toby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch2_room_cyber_battle_maze_2`,
  `obj_checkmarktreasurebox`, `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markeru`,
  `obj_markerv`, `obj_markerw`, `obj_readable_room1`, `obj_soliddark`,
  `obj_treasure_room`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_battle_maze_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_cyber_teacup_2
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_escalator_slide`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_doorW`,
  `obj_mainchara`, `obj_markerA`, `obj_markert`, `obj_queenscreen`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_cyber_nuberts_treasure resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_intro_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_cyber_intro_1`, `obj_cyber_light`,
  `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`,
  `obj_cyber_wall_lights_right`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerB`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_intro_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene9`, `obj_cyber_wall_lights`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_npc_room`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_cyber_intro_connector resolves room_goto_next via scr_get_room_by_id
  asset order; enabled placed obj_doorB from room_dw_cyber_rhythm_slide resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_intro_connector`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; conditional.
- Important controllers: `obj_cyber_light`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_darkcontroller`, `obj_darkslide_new`,
  `obj_doorA`, `obj_doorAny`, `obj_hangplug`, `obj_mainchara`, `obj_markerAny`,
  `obj_npc_room`, `obj_npc_room_animated`, `obj_overworld_bulletarea`,
  `obj_savepoint`, `obj_solidblocksized`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorB from room_dw_cyber_intro_2
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.plot < 51).

### Chapter 2: `room_dw_cyber_keyboard_puzzle_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_camera_area`, `obj_ch2_keyboardpuzzle_controller`,
  `obj_ch2_keyboardpuzzle_tile`, `obj_controller_keyboard_puzzle_1`,
  `obj_cyber_hole_lights`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorB`, `obj_forcefield`, `obj_mainchara`,
  `obj_markerA`, `obj_musicer_cyber`, `obj_npc_room`, `obj_nubertQueenScreen`,
  `obj_parallaxer_cyber_2`, `obj_solidblocksized`, `obj_traffic_road_trigger`,
  `obj_treasure_room`.
- Incoming transitions: placed obj_ch2_keyboardpuzzle_controller; context
  runtime controller explicitly checks room_dw_cyber_keyboard_puzzle_1.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: checks global.flag\[390\] == 1 for puzzle completion state; if
  (global.flag\[390\] == 1).

### Chapter 2: `room_dw_cyber_keyboard_puzzle_1_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch2_keyboardpuzzle_controller`,
  `obj_ch2_keyboardpuzzle_speaker`, `obj_ch2_keyboardpuzzle_tile`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_keyboard_puzzle_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_keyboardpuzzle_controller`,
  `obj_ch2_keyboardpuzzle_tile`, `obj_controller_keyboard_puzzle_2`,
  `obj_cyber_hole_lights`, `obj_cyber_light_standalone`,
  `obj_cyber_wall_lights`, `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_musicer_cyber`, `obj_solidblocksized`,
  `obj_traffic_road_trigger`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_maze_virokun
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_keyboard_puzzle_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_keyboardpuzzle_controller`,
  `obj_controller_keyboard_puzzle_3`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`, `obj_markerw`,
  `obj_musicer_cyber`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_traffic_road_trigger`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_cyber_battle_maze_3 resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_keyboardexample`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch2_keyboardpuzzle_controller`,
  `obj_ch2_keyboardpuzzle_tile`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_maze_fireworks`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_cyber_maze_fireworks`,
  `obj_cyber_shadowMaker_fireworks`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorW`, `obj_firework_cityscape`,
  `obj_fireworks_manager`, `obj_mainchara`, `obj_markeru`, `obj_musicer_cyber`,
  `obj_parallaxer_cyber_2`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_maze_queenscreen`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_dw_cyber_maze_queenscreen`,
  `obj_conveyorbelt`, `obj_cyber_tree_spin`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorW`, `obj_mainchara`,
  `obj_markerB`, `obj_markeru`, `obj_musicer_cyber`, `obj_npc_room`,
  `obj_npc_sign`, `obj_parallaxer_cyber_2`, `obj_solidblocksized`,
  `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorB from room_dw_cyber_viro_ring
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_maze_rhythm`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_beatbulletroom`, `obj_conveyorbelt`,
  `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`, `obj_markert`,
  `obj_markerw`, `obj_musicer_cyber`, `obj_overworld_bulletarea`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_cyber_shaunsmusicalbullettunnel resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_cyber_escalator_slide resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_maze_tasque`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cyber_light`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorW`, `obj_dw_cyber_maze_tasque_controller`,
  `obj_mainchara`, `obj_markert`, `obj_musicer_cyber`, `obj_queenscreen`,
  `obj_readable_room1`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_treasure_room`, `obj_triggervolume`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_maze_virokun`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_beatbulletroom`, `obj_beatFlashOW`,
  `obj_chaseenemy`, `obj_controller_dw_cyber_maze_virokun`,
  `obj_cyber_tree_spin`, `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`,
  `obj_cyber_wall_lights_right`, `obj_cybercity_bg_sign`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_doorW`, `obj_forcefield`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_markert`,
  `obj_markeru`, `obj_musicer_cyber`, `obj_overworld_bulletarea`,
  `obj_queenscreen_dance`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_viroarrow`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_musical_door
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_cyber_keyboard_puzzle_2 resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[333\] == 0).

### Chapter 2: `room_dw_cyber_maze_virokun_backuo`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markert`, `obj_markeru`, `obj_queenscreen`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_music_bullet`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_beatbulletroom`, `obj_beatFlashOW`,
  `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`,
  `obj_cyber_wall_lights_right`, `obj_darkcontroller`, `obj_darkslide_new`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_cyber`, `obj_npc_room`, `obj_overworld_bulletarea`,
  `obj_parallaxer_cyber_2`, `obj_solidblocksized`,
  `obj_sweet_dw_cyber_music_bullet`, `obj_teacup`, `obj_teacup_landingspot`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_cyber_battle_maze_1 resolves room_goto_next via scr_get_room_by_id
  asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_music_bullet_original`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_music_fight`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_cyber01`, `obj_cyber_music_battleBullets`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_markerA`,
  `obj_MovingPlat_dw_cyber_music_final`, `obj_musicer_cyber`,
  `obj_overworld_bulletarea`, `obj_parallaxer_cyber`.
- Incoming transitions: placed obj_ch2_cyber01 and obj_cyber_music_battleBullets
  drive the overworld music-fight sequence.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_music_final`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_ch2_cyber01`,
  `obj_controller_dw_cyber_music_final`, `obj_cyber_light_standalone`,
  `obj_cyber_music_battleBullets`, `obj_cyber_tree_spin`,
  `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`,
  `obj_cyber_wall_lights_right`, `obj_darkcontroller`, `obj_doorB`, `obj_doorW`,
  `obj_fakeWalkway_dw_cyber_music_final`, `obj_mainchara`, `obj_markerA`,
  `obj_markert`, `obj_MovingPlat_dw_cyber_music_final`,
  `obj_solidblock_destructable`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_cyber_battle_maze_2 resolves room_goto_next via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.plot < 60).

### Chapter 2: `room_dw_cyber_musical_door`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_cyber_light`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorW`, `obj_forcefield`,
  `obj_mainchara`, `obj_markerA`, `obj_markerAny`, `obj_markerB`, `obj_markert`,
  `obj_musicer_cyber`, `obj_npc_musical_door`, `obj_shortcut_door`,
  `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_queen_boxing
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_cyber_maze_virokun resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.plot >= 60).

### Chapter 2: `room_dw_cyber_musical_shop`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch2_room_cyber_shop`,
  `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`,
  `obj_cyber_wall_lights_right`, `obj_darkcontroller`, `obj_doorW`,
  `obj_doorX_musfade`, `obj_mainchara`, `obj_markerAny`, `obj_markert`,
  `obj_markeru`, `obj_musicer_cyber`, `obj_savepoint`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_nuberts_treasure`

- Area: Cyber Field.
- Runtime role/status: Nubert treasure side room driven by obj_treasure_room;
  conditional.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_room`, `obj_nubertQueenScreen`, `obj_readable_room1`,
  `obj_solidblock`, `obj_treasure_room`.
- Incoming transitions: placed obj_treasure_room and obj_doorB; treasure context
  runtime controller and ordered door route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.plot >= 100).

### Chapter 2: `room_dw_cyber_post_music_boss_slide`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; verified production reachable.
- Important controllers: `obj_camera_area`,
  `obj_controller_dw_cyber_post_music_boss_slide`, `obj_conveyorbelt`,
  `obj_cyber_light`, `obj_cyber_shadowMaker_fireworks`, `obj_cyber_tree_spin`,
  `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`,
  `obj_cyber_wall_lights_right`, `obj_darkcontroller`, `obj_darkslide_new`,
  `obj_doorW`, `obj_fireworks_manager`, `obj_magicalglass`, `obj_mainchara`,
  `obj_markert`, `obj_markerw`, `obj_musicer_cyber`, `obj_npc_sign`,
  `obj_parallaxer_cyber_2`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_queen_boxing`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene10`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorD`, `obj_mainchara`,
  `obj_markerB`, `obj_markerC`, `obj_musicer_cyber`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorB from room_dw_cyber_musical_door
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_rhythm_slide`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cyber_wall_lights`, `obj_darkcontroller`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_musicalslide`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_intro_2
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_rollercoaster`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene11a`, `obj_ch2_scene11a_bg`,
  `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_teacup_final
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_savepoint`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_cyber_light`, `obj_cyber_light_standalone`,
  `obj_cyber_wall_lights`, `obj_cyber_wall_lights_left`, `obj_darkcontroller`,
  `obj_doorA`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_cyber`, `obj_parallaxer_cyber_2`, `obj_savepoint`,
  `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_cyber_battle_maze_1 resolves room_goto_previous via scr_get_room_by_id
  asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_savepoint_original`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging;
  uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_savepoint`,
  `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_shaunsmusicalbullettunnel`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_beatbulletroomexample`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_overworld_bulletarea`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_teacup_2
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_tasque_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_cyber_tree_spin`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_musicer_cyber`,
  `obj_npc_room`, `obj_npc_sign`, `obj_parallaxer_cyber_2`, `obj_queenscreen`,
  `obj_solidblocksized`, `obj_solidenemy`, `obj_triggervolume`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_tasque_battle_og`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorB`,
  `obj_doorC`, `obj_dw_cyber_tasque_battle_controller`, `obj_forcefield`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerD`,
  `obj_musicer_cyber`, `obj_npc_room`, `obj_queenscreen`, `obj_readable_room1`,
  `obj_solidblocksized`, `obj_solidenemy`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_teacup_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markeru`,
  `obj_soliddark`, `obj_teacup`, `obj_teacup_landingspot`,
  `obj_teacup_reverser`.
- Incoming transitions: enabled placed obj_doorB from room_dw_cyber_viromaze2
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_teacup_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_cyber_battle_maze_3 resolves room_goto_next via scr_get_room_by_id
  asset order; enabled placed obj_doorB from
  room_dw_cyber_shaunsmusicalbullettunnel resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_teacup_final`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_room_dw_cyber_teacup_final`,
  `obj_cyber_teacup_parallaxer`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorA_musfade`, `obj_doorAny`,
  `obj_doorW`, `obj_mainchara`, `obj_markerB`, `obj_markerw`,
  `obj_musicer_cyber`, `obj_npc_sign`, `obj_solidblock_destructable`,
  `obj_solidblocksized`, `obj_teacup`, `obj_teacup_landingspot`,
  `obj_teacup_scoreboard`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_cyber_rollercoaster resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: to room_dw_cyber_viro_ring.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_cyber_viro_ring`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_cyber_tree_spin`, `obj_cyber_wall_lights`,
  `obj_cyber_wall_lights_left`, `obj_cyber_wall_lights_right`,
  `obj_darkcontroller`, `obj_doorB`, `obj_doorW`, `obj_forcefield`,
  `obj_mainchara`, `obj_markerA`, `obj_markerAny`, `obj_markerX`,
  `obj_musicer_cyber`, `obj_overworld_bulletarea`, `obj_ow_viroring`,
  `obj_ow_viroringTrig`, `obj_queenscreen`, `obj_queenscreen_dance`,
  `obj_solidblocksized`, `obj_traffic_road_trigger`, `obj_viroring_controller`.
- Incoming transitions: door from room_dw_cyber_teacup_final; enabled placed
  obj_doorA from room_dw_cyber_maze_queenscreen resolves room_goto_next via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[352\] == 1); if (global.flag\[123\] == 1); if
  (global.flag\[352\] == 1); if (global.flag\[427\] != 0).

### Chapter 2: `room_dw_cyber_viromaze2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_controller_dw_cyber_viromaze2`,
  `obj_darkcontroller`, `obj_doorB`, `obj_forcefield`, `obj_mainchara`,
  `obj_markerA`, `obj_overworld_bulletarea`, `obj_ow_viromaze2_viro`,
  `obj_queenscreen`, `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_dw_cyber_teacup_1
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[352\] == 1); if (global.flag\[123\] == 1).

### Chapter 2: `room_dw_cyber_virovirokun_fight`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_conveyorbelt`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_doorB`, `obj_dw_cyber_virovirokun_fight_controller`,
  `obj_mainchara`, `obj_markerA`, `obj_overworld_bulletarea`,
  `obj_ow_enemy_virovirokun`, `obj_ow_virovirokunswitch`, `obj_queenscreen`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: placed obj_dw_cyber_virovirokun_fight_controller drives
  the Virovirokun overworld encounter.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_acid_tunnel`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene21`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorW`, `obj_gradientglow`, `obj_mainchara`, `obj_markerB`,
  `obj_markerX`, `obj_npc_acid_house`, `obj_sdl_dark`, `obj_sdr_dark`,
  `obj_solidblocksized`, `obj_sul_dark`, `obj_sur`, `obj_sur_dark`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_mansion_acid_tunnel_puzzle_entrance resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_acid_tunnel_exit`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene23a`, `obj_ch2_scene24e`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB_musfade`, `obj_mainchara`,
  `obj_mansion_vase`, `obj_markerA`, `obj_markerB`, `obj_musicer_mansion_top`,
  `obj_parallaxer_mansion`, `obj_sdr_dark`, `obj_solidblocksized`,
  `obj_sul_dark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_mansion_acid_tunnel_loop_rouxls resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_mansion_east_4f_b resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_acid_tunnel_loop_rouxls`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene21_loop`, `obj_ch2_scene21_loop_vfx`,
  `obj_darkcontroller`, `obj_doorA_musfade`, `obj_doorB`, `obj_gradientglow`,
  `obj_mainchara`, `obj_mansion_vase`, `obj_markerA`, `obj_markerB`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_mansion_acid_tunnel_puzzle_entrance resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_mansion_acid_tunnel_exit resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_acid_tunnel_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch2_scene21`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorW`, `obj_mainchara`, `obj_markerB`, `obj_markerX`,
  `obj_queencar_talktrigger`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_acid_tunnel_puzzle_entrance`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene21_puzzle_entrance`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorW`,
  `obj_gradientglow`, `obj_mainchara`, `obj_markerA`, `obj_markerAny`,
  `obj_markerB`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_mansion_acid_tunnel resolves room_goto_next via scr_get_room_by_id
  asset order; enabled placed obj_doorB from
  room_dw_mansion_acid_tunnel_loop_rouxls resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_central`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; conditional.
- Important controllers: `obj_ch2_room_mansion_b_central`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_doorW`, `obj_forcefield`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerX`, `obj_musicer_mansion_basement`,
  `obj_savepoint`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_b_stairs
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_b_west_1f resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[373\] == 1).

### Chapter 2: `room_dw_mansion_b_east`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_area`, `obj_ch2_sceneex2`,
  `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`, `obj_markerAny`,
  `obj_markerX`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_east_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_sceneex2a`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_markerv`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_east_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_sceneex2_mus`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerw`, `obj_npc_room_animated`,
  `obj_readable_room1`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_east_transformed`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerX`, `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_entrance`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_sceneex3`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorw_musfade`, `obj_mainchara`, `obj_markerB`, `obj_markert`,
  `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_mansion_b_stairs
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_stairs`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_b_entrance
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_b_central resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_west_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_doorW`,
  `obj_mainchara`, `obj_mansion_basement_door`, `obj_markerA`, `obj_markerAny`,
  `obj_overworld_bulletarea`, `obj_solidblocksized`, `obj_wallplug`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_b_central
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_west_1f_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bug_treasure_chest`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerv`, `obj_solidblocksized`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_west_1f_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bug_treasure_chest`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerw`, `obj_solidblocksized`,
  `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_b_west_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_area`,
  `obj_controller_dw_mansion_b_west_2f`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_markerX`, `obj_musicer_mansion_basement`,
  `obj_readable_room1`, `obj_solidblocksized`, `obj_teacup`,
  `obj_teacup_bullet`, `obj_teacup_landingspot`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_bridges`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_bridgeSwappable`, `obj_bridgeSwapper`,
  `obj_camera_area`, `obj_chaseenemy`, `obj_controller_dw_mansion_bridges`,
  `obj_darkcontroller`, `obj_doorW`, `obj_gradientglow`, `obj_mainchara`,
  `obj_markert`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_readable_room1`, `obj_solidblocksized`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[343\] == 0).

### Chapter 2: `room_dw_mansion_bridges_funny`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bridgeSwappable`, `obj_bridgeSwapper`,
  `obj_bridgeSwapper_decoy`, `obj_controller_dw_mansion_bridges_funny`,
  `obj_darkcontroller`, `obj_doorW`, `obj_gradientglow`, `obj_mainchara`,
  `obj_markerX`, `obj_queenstatue_acid`, `obj_solidblocksized`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_bridgesold`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_bridgeSwappable`, `obj_bridgeSwapper`,
  `obj_chaseenemy`, `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerv`, `obj_markerw`, `obj_markerX`, `obj_solidblocksized`,
  `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_darkbulb_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene19a`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_mansion_vase`, `obj_markert`, `obj_markeru`,
  `obj_readable_room1`, `obj_shapepuzzle`, `obj_shapepuzzlebutton`,
  `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_darkbulb_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene19b`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_mansion_vase`, `obj_markers`, `obj_markert`,
  `obj_readable_room1`, `obj_shapepuzzle`, `obj_shapepuzzlebutton`,
  `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_darkbulb_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene19c`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_mansion_vase`, `obj_markers`, `obj_markert`,
  `obj_readable_room1`, `obj_shapepuzzle`, `obj_shapepuzzlebutton`,
  `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_dining_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_dining`, `obj_ch2_scene20`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorW`, `obj_mainchara`,
  `obj_mansion_candleabra`, `obj_mansion_chandelier`, `obj_mansion_plate`,
  `obj_mansion_vase`, `obj_markerB`, `obj_markert`, `obj_sdr_dark`,
  `obj_solidblocksized`, `obj_sul_dark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_mansion_entrance
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_dining_storage`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_mansion_vase`, `obj_mansion_waterbottle`, `obj_markerX`,
  `obj_readable_room1`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorB from room_dw_mansion_east_1f_b
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_dining_storage_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_sign`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_dining3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_dining3`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markeru`, `obj_markerX`, `obj_mazepipis`,
  `obj_readable_room1`, `obj_solidblocksized`, `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_dininghall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_battlealphaer`, `obj_camera_area`,
  `obj_controller_dininghall`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_mansion_chandelier`, `obj_mansion_vase`, `obj_markeru`,
  `obj_markerw`, `obj_markerX`, `obj_musicer_mansion`,
  `obj_overworld_bulletarea`, `obj_pipisFireworkGenerator`, `obj_saucer`,
  `obj_scarableSwatch`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[382\] == 0); if (global.flag\[382\] == 0); if
  (global.flag\[382\] == 0).

### Chapter 2: `room_dw_mansion_east_1f_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_dw_mansion_east_1f_a`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB_musfade`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_musicer_mansion`, `obj_queenvase`,
  `obj_readable_room1`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_mansion_east_2f_teacup resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_1f_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_soliddark`.
- Incoming transitions: placed obj_doorB resolves ordered Mansion route via
  ordered room route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_1f_c`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerX`,
  `obj_musicer_mansion`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_east_1f_d
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_sparks resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_1f_d`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_controller_dw_mansion_east_1f_d`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_musicer_mansion`,
  `obj_overworld_bulletarea`, `obj_queenscreen`, `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorB from room_dw_mansion_east_1f_c
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[354\] == 1).

### Chapter 2: `room_dw_mansion_east_1f_e`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_east_1f_e`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorB`, `obj_mainchara`, `obj_mansion_art_frame`,
  `obj_mansion_candleabra`, `obj_mansion_chandelier`, `obj_mansion_plate`,
  `obj_mansion_statue`, `obj_markerA`, `obj_markerB`, `obj_readable_room1`,
  `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_traffic
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_east_1f_secret resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_1f_secret`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_east_1f_secret`,
  `obj_ch2_sceneex1`, `obj_darkcontroller`, `obj_doorAny`, `obj_doorB`,
  `obj_doorw_musfade`, `obj_mainchara`, `obj_mansion_chandelier`,
  `obj_mansion_doorframe_left_side`, `obj_mansion_doorframe_left_top`,
  `obj_mansion_doorframe_right_side`, `obj_mansion_doorframe_right_top`,
  `obj_mansion_keygen_lock`, `obj_mansion_switch`, `obj_mansion_vase`,
  `obj_markerAny`, `obj_markeru`, `obj_musicer_mansion`, `obj_readable_room1`,
  `obj_solidblocksized`, `obj_weirdroute_manipulator`.
- Incoming transitions: door from room_dw_mansion_entrance; enabled placed
  obj_doorA from room_dw_mansion_east_1f_e resolves room_goto_next via
  scr_get_room_by_id asset order; runtime dispatch; runtime dispatch; runtime
  dispatch.
- Outgoing transitions: to room_dw_mansion_entrance.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_battlealphaer`, `obj_battleLayerHighlight`,
  `obj_ch2_room_mansion_east_2f_a`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorW`, `obj_mainchara`, `obj_mansion_art_frame`,
  `obj_mansion_chandelier`, `obj_mansion_vase`, `obj_markerAny`, `obj_markerw`,
  `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_mansion_east_2f_transformed_new resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_c`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_mansion_chandelier`, `obj_mansion_vase`, `obj_markerAny`, `obj_markert`,
  `obj_markeru`, `obj_queenvaseonwheels`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_c_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_east_2f_c_a`,
  `obj_darkcontroller`, `obj_doorW`, `obj_hangplug`, `obj_mainchara`,
  `obj_mansion_vase`, `obj_markerv`, `obj_markerw`, `obj_overworld_bulletarea`,
  `obj_saucer`, `obj_solidblocksized`, `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_c_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerX`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_d`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_doorW`,
  `obj_mainchara`, `obj_mansion_stanchion`, `obj_markert`, `obj_markerX`,
  `obj_musicer_mansion`, `obj_musictracker`, `obj_overworld_bulletarea`,
  `obj_queenart_mona`, `obj_queenstatue_parallax`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: door from room_dw_mansion_east_teacup_4; runtime
  dispatch.
- Outgoing transitions: to room_dw_mansion_east_teacup_4.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_d_backup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markert`, `obj_markerX`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_shortcut`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_battlealphaer`, `obj_battleLayerHighlight`,
  `obj_ch2_room_mansion_2f_shortcut`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_doorB`, `obj_mainchara`, `obj_markerA`, `obj_markert`,
  `obj_musicer_mansion`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_mansion_entrance; enabled placed
  obj_doorA from room_dw_mansion_east_2f_transformed_new resolves room_goto_next
  via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: to room_dw_mansion_entrance.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_teacup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerv`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_east_1f_a
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_east_4f_e resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_transformed_new`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_dw_mansion_east_2f_transformed_new`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorW`,
  `obj_lockedDoor_mansion_east_2f_transformed_new`, `obj_mainchara`,
  `obj_mansion_chandelier`, `obj_mansion_vase`, `obj_markerA`, `obj_markerAny`,
  `obj_markerB`, `obj_musicer_mansion`, `obj_musictracker`, `obj_npc_sign`,
  `obj_overworld_bulletarea`, `obj_queenart_mona`, `obj_queenart_red`,
  `obj_readable_room1`, `obj_solidblock_destructable`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_east_2f_a
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_east_2f_shortcut resolves room_goto_previous
  via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_2f_ufo_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_activator_mansion_east_2f_transformed_new`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorW`,
  `obj_lockedDoor_mansion_east_2f_transformed_new`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markeru`, `obj_markerv`,
  `obj_overworld_bulletarea`, `obj_readable_room1`, `obj_saucer`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[382\] == 0).

### Chapter 2: `room_dw_mansion_east_3f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_3f`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_doorW`, `obj_mainchara`, `obj_mansion_vase`,
  `obj_markerAny`, `obj_markeru`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_mansion`, `obj_solidblocksized`, `obj_weirdroute_manipulator`.
- Incoming transitions: door from room_dw_mansion_east_4f_b; door from
  room_dw_mansion_east_teacup_4; door from room_dw_mansion_entrance; runtime
  dispatch.
- Outgoing transitions: to room_dw_mansion_east_4f_b; to
  room_dw_mansion_east_teacup_4; to room_dw_mansion_entrance.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_3f_projection`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_projection`,
  `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`, `obj_markeru`,
  `obj_projector_footage`, `obj_shadowMaker`, `obj_solidblocksized`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_3f_toilet`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_room`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_4f_a`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB_musfade`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markers`,
  `obj_savepoint`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_east_4f_e
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_4f_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_east_4f_b`,
  `obj_ch2_scene_sideb_noelleroom`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorAny`, `obj_doorB`, `obj_mainchara`, `obj_mansion_chandelier`,
  `obj_mansion_vase`, `obj_markerA`, `obj_markerAny`, `obj_markerB`,
  `obj_musicer_mansion_top`, `obj_parallaxer_mansion`, `obj_solidblocksized`,
  `obj_traffic_road_trigger`, `obj_weirdroute_manipulator`.
- Incoming transitions: door from room_dw_mansion_east_3f; enabled placed
  obj_doorA from room_dw_mansion_acid_tunnel_exit resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_mansion_east_4f_c resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: to room_dw_mansion_east_3f; to
  room_dw_mansion_noelle_room.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_4f_c`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_hangplug`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_overworld_bulletarea`, `obj_parallaxer_mansion`, `obj_solidblocksized`,
  `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_east_4f_b
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_east_4f_d resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_4f_d`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_ch2_scene25`, `obj_ch2_scene25_fountain`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_parallaxer_mansion`, `obj_sdr_dark`,
  `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_east_4f_c
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_top resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_4f_e`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_mansion_east_4f_a
  resolves room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_teacup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_mansion_vase`, `obj_markerAny`, `obj_markerX`, `obj_solidblocksized`,
  `obj_teacup`, `obj_teacup_landingspot`, `obj_teacup_reverser`,
  `obj_teacupParallaxer`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_teacup_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_mansion_vase`, `obj_markerAny`, `obj_markerX`, `obj_solidblocksized`,
  `obj_teacup`, `obj_teacup_landingspot`, `obj_teacup_reverser`,
  `obj_teacupParallaxer`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_mansion_east_teacup_3 resolves room_goto_next via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_teacup_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_mansion_vase`, `obj_markerA`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_teacup`, `obj_teacup_landingspot`,
  `obj_teacup_reverser`, `obj_teacupParallaxer`.
- Incoming transitions: placed obj_teacupParallaxer; context runtime controller
  explicitly handles the Mansion teacup route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_teacup_4`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_mansion_vase`, `obj_markerAny`, `obj_solidblocksized`, `obj_teacup`,
  `obj_teacup_landingspot`, `obj_teacup_reverser`, `obj_teacupParallaxer`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: door from room_dw_mansion_east_2f_d; door from
  room_dw_mansion_east_3f; enabled placed obj_doorB from
  room_dw_mansion_east_teacup_3 resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: to room_dw_mansion_east_2f_d; to
  room_dw_mansion_east_3f.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_east_teacup_4_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`, `obj_teacup`,
  `obj_teacup_landingspot`, `obj_teacup_reverser`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_elevator`

- Area: Mansion.
- Runtime role/status: Elevator travel and floor-selection staging verified in
  the mansion elevator controller flow; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerX`, `obj_soliddark`.
- Incoming transitions: placed obj_doorW; mansion elevator dispatch context
  runtime controller.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_entrance`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; conditional.
- Important controllers: `obj_ch2_room_mansion_entrance`,
  `obj_cybercity_bg_screen`, `obj_darkcontroller`, `obj_doorA_musfade`,
  `obj_doorAny`, `obj_doorB`, `obj_doorw_musfade`, `obj_forcefield`,
  `obj_mainchara`, `obj_markerA`, `obj_markerAny`, `obj_markerB`, `obj_markeru`,
  `obj_musicer_mansion_entrance`, `obj_npc_sign`, `obj_queenscreen`,
  `obj_savepoint`, `obj_sdl_dark`, `obj_sdr_dark`, `obj_shortcut_door`,
  `obj_soliddark`, `obj_sul_dark`, `obj_sur_dark`, `obj_triggervolume`,
  `obj_weirdroute_manipulator`.
- Incoming transitions: door from room_dw_mansion_east_1f_secret; door from
  room_dw_mansion_east_2f_shortcut; door from room_dw_mansion_east_3f; enabled
  placed obj_doorA from room_dw_mansion_dining_a resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_mansion_fire_paintings resolves room_goto_previous via
  scr_get_room_by_id asset order; runtime dispatch; runtime dispatch; runtime
  dispatch.
- Outgoing transitions: to room_dw_mansion_east_1f_secret; to
  room_dw_mansion_east_2f_shortcut; to room_dw_mansion_east_3f.
- Conditions: if (global.flag\[916\] != 0 || global.flag\[915\] < 6); if
  (global.flag\[916\] != 0 || global.flag\[915\] < 6).

### Chapter 2: `room_dw_mansion_ferris_wheel`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene23c`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_ferris_wheel_post`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene23d`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_fire_paintings`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_controller_dw_mansion_fire_paintings`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB_musfade`, `obj_mainchara`,
  `obj_mansion_chandelier`, `obj_mansion_vase`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_mansion`, `obj_musictracker`, `obj_overworld_bulletarea`,
  `obj_queenart_mona`, `obj_queenart_red`, `obj_sdl_dark`,
  `obj_solidblocksized`, `obj_sur_dark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_entrance
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_single_pot resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[399\] == 1); if (global.flag\[398\] == 1).

### Chapter 2: `room_dw_mansion_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkfountain`,
  `obj_fountainkris_ch2_sideb`, `obj_mainchara`.
- Incoming transitions: placed obj_darkfountain; context runtime controller
  explicitly handles room_dw_mansion_fountain.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_gigaqueen`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `o_boxingcontroller`, `o_boxingqueen`,
  `obj_3d_bg_effect`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_hands`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_bridgeSwappable`, `obj_bridgeSwapper`,
  `obj_camera_area`, `obj_controller_mansion_hands`, `obj_darkcontroller`,
  `obj_doorB`, `obj_doorW`, `obj_gradientglow`, `obj_mainchara`, `obj_markerA`,
  `obj_markerX`, `obj_npc_sign`, `obj_sdl`, `obj_sdl_dark`, `obj_sdr`,
  `obj_sdr_dark`, `obj_solidblocksized`, `obj_soliddark`, `obj_sul_dark`,
  `obj_sur_dark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_mansion_mouseLottery resolves room_goto_next via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[343\] == 1); if (global.flag\[343\] == 1).

### Chapter 2: `room_dw_mansion_kitchen`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_mansion_kitchen`, `obj_darkcontroller`,
  `obj_doorW`, `obj_mainchara`, `obj_markerv`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_krisroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene17b`, `obj_ch2_scene17b_lancer_type`,
  `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`, `obj_markers`,
  `obj_markerv`, `obj_npc_mansion_room`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_lightner_hallway`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch2_scene18`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_mansion_door`, `obj_mansion_shovelpile`,
  `obj_mansion_vase`, `obj_markerAny`, `obj_markeru`,
  `obj_musicer_mansion_entrance`, `obj_readable_room1`, `obj_savepoint`,
  `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_mouseLottery`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_bridgeSwappable`, `obj_bridgeSwapper`,
  `obj_camera_area`, `obj_darkcontroller`, `obj_doorA`, `obj_doorW`,
  `obj_dw_mansion_mouseLottery_Chest`, `obj_gradientglow`,
  `obj_lottery_bridgeBuilder1`, `obj_lottery_holemouse_generator`,
  `obj_lotterymouseController`, `obj_lotteryMouseTrigger`, `obj_mainchara`,
  `obj_markerB`, `obj_markerX`, `obj_npc_sign`, `obj_solidblocksized`,
  `obj_soliddark`, `obj_solidenemy`.
- Incoming transitions: enabled placed obj_doorB from room_dw_mansion_hands
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[378\] == 0); if (global.flag\[377\] == 0); if
  (global.flag\[378\] == 1); if (global.flag\[377\] == 1); if
  (global.flag\[377\] == 0); if (global.flag\[377\] == 0); if
  (global.flag\[377\] == 0); if (global.flag\[378\] == 0); if
  (global.flag\[378\] == 0); if (global.flag\[378\] == 0).

### Chapter 2: `room_dw_mansion_noelle_room`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene23b`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_markerX`, `obj_readable_room1`, `obj_sdr_dark`,
  `obj_soliddark`.
- Incoming transitions: door from room_dw_mansion_east_4f_b; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_potBalance`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_dw_mansion_potBalance`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_mansion_art_frame`, `obj_mansion_chandelier`, `obj_mansion_vase`,
  `obj_markerA`, `obj_markerB`, `obj_npc_butler`, `obj_queenvase`,
  `obj_racingline`, `obj_solidblocksized`, `obj_triggervolume`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_single_pot
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_tasquePaintings resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_prefountain`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch2_scene26_cityscape`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorAny`, `obj_mainchara`, `obj_markerA`,
  `obj_readable_room1`, `obj_savepoint`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_mansion_top.
- Outgoing transitions: to room_dw_mansion_top.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_single_pot`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_dw_mansion_single_pot`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_mansion_art_frame`, `obj_markerA`, `obj_markerB`, `obj_queenvase`,
  `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_mansion_fire_paintings resolves room_goto_next via scr_get_room_by_id
  asset order; enabled placed obj_doorB from room_dw_mansion_potBalance resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_sparks`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_hangplug`,
  `obj_mainchara`, `obj_markerA`, `obj_overworld_bulletarea`,
  `obj_solidblocksized`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_east_1f_c
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_susieroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markert`, `obj_markerv`, `obj_npc_mansion_room`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_tasquePaintings`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_controller_tasquePaintingsRevisit`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_mainchara`,
  `obj_mansion_chandelier`, `obj_mansion_vase`, `obj_markerA`, `obj_markerB`,
  `obj_musicer_mansion`, `obj_npc_tasquemanager`, `obj_solidblocksized`,
  `obj_tasquepainting`.
- Incoming transitions: enabled placed obj_doorA from room_dw_mansion_potBalance
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_dw_mansion_traffic resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_top`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene26`, `obj_ch2_scene26_cityscape`,
  `obj_ch2_scene26_gigaqueen`, `obj_ch2_scene26_wall`,
  `obj_ch2_scene27_queenhand`, `obj_darkcontroller`, `obj_doorAny`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_soliddark`.
- Incoming transitions: door from room_dw_mansion_prefountain; enabled placed
  obj_doorA from room_dw_mansion_east_4f_d resolves room_goto_next via
  scr_get_room_by_id asset order; enabled placed obj_doorB from
  room_dw_mansion_top_post resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: to room_dw_mansion_prefountain.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_top_post`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene26_cityscape`,
  `obj_ch2_scene26_gigaqueen`, `obj_ch2_scene26_wall`, `obj_ch2_scene27`,
  `obj_ch2_scene27_queenhand`, `obj_darkcontroller`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_top_post_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch2_scene27`, `obj_darkcontroller`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_mansion_traffic`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_carKiller`, `obj_charmarker`,
  `obj_controller_mansion_traffic`, `obj_cybercity_bg_sign`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorB`, `obj_doorW`,
  `obj_dw_mansion_traffic_overhang`, `obj_forcefield`,
  `obj_holemouse_generator`, `obj_holemouse_invis_counterclockwise`,
  `obj_mainchara`, `obj_mansion_art_frame`, `obj_mansion_chandelier`,
  `obj_mansion_doorframe_left_side`, `obj_mansion_doorframe_left_top`,
  `obj_mansion_doorframe_right_side`, `obj_mansion_doorframe_right_top`,
  `obj_mansion_stanchion`, `obj_mansion_vase`, `obj_markerA`, `obj_markerAny`,
  `obj_markerB`, `obj_mouseTrigger`, `obj_readable_room1`, `obj_roadcrossing`,
  `obj_solidblock_destructable`, `obj_solidblocksized`,
  `obj_traffic_car_generator`, `obj_traffic_road_trigger`, `obj_traffic_switch`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_mansion_tasquePaintings resolves room_goto_next via scr_get_room_by_id
  asset order; enabled placed obj_doorB from room_dw_mansion_east_1f_e resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: if (global.flag\[370\] == 1); if (global.flag\[370\] == 0); if
  (global.flag\[370\] == 1); if (global.flag\[370\] == 0); if
  (global.flag\[370\] == 0).

### Chapter 2: `room_dw_mansion_traffic_original`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_carKiller`, `obj_carTurner`, `obj_charmarker`,
  `obj_controller_mansion_traffic_old`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorB`, `obj_holemouse_generator`,
  `obj_holemouse_invis_counterclockwise`, `obj_mainchara`, `obj_markerA`,
  `obj_markerB`, `obj_mouseTrigger`, `obj_musicer_mansion`,
  `obj_solidblocksized`, `obj_traffic_car_generator`, `obj_traffic_switch`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_ralsei_castle_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_cauldron_glow`, `obj_ch2_room_castle_1f`,
  `obj_ch2_room_castle_1f_cake`, `obj_darkcontroller`, `obj_doorA`, `obj_doorW`,
  `obj_mainchara`, `obj_markerB`, `obj_markerw`, `obj_markerX`,
  `obj_npc_room_animated`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_ralsei_castle_2f
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_ralsei_castle_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_castle_2f`, `obj_darkcontroller`,
  `obj_doorB`, `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerv`,
  `obj_markerw`, `obj_markerX`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_ralsei_castle_1f
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_dw_ralsei_castle_front`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_torch`, `obj_darkcontroller`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerX`, `obj_npc_room`,
  `obj_npc_room_animated`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from
  room_dw_castle_area_2_transformed resolves room_goto_next via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_ed`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_credits_2`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_empty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 2: `room_flowershop_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorX`, `obj_flowershop_event`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorB from room_flowershop_2f
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_flowershop_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_flowershop_event`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_sign`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_flowershop_1f
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_gameover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_gameover_init`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_gif_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_sprite_catalog`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_gms_debug_failsafe`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_gamecontroller`, `obj_gms_debug_failsafe`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_GMS2_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_soliddark`, `obj_swordarea`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_graveyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_town_graveyard`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerX`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sur`, `obj_town_event`.
- Incoming transitions: enabled placed obj_doorA from room_town_church resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_hospital_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene_hospital_sideb`, `obj_doorA`,
  `obj_doorB`, `obj_doorC`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerD`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_hospital_lobby
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_hospital_rudy resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_hospital_lobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorW`, `obj_mainchara`,
  `obj_markerB`, `obj_markerw`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorB from room_hospital_hallway
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_hospital_room2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_hospital_rudy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_room_town_hospital`, `obj_doorB`,
  `obj_mainchara`, `obj_markerA`, `obj_npc_rudy`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_hospital_hallway
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `ROOM_INITIALIZE`

- Area: Bootstrap.
- Runtime role/status: runtime initialization room; bootstrap.
- Important controllers: `obj_debugProfiler`, `obj_gamecontroller`,
  `obj_initializer2`, `obj_jean_debug`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 2: `room_insidecloset`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_intro_ch2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_intro_ch2`.
- Incoming transitions: runtime variable dispatch to room_intro_ch2; runtime
  variable dispatch to room_intro_ch2.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_krishallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_doorC`, `obj_hallway_mirror`,
  `obj_mainchara`, `obj_markerA`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_solidlong`.
- Incoming transitions: enabled placed obj_doorA from room_krisroom resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_krisroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_krisroom`, `obj_mainchara`,
  `obj_markerB`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorB from room_krishallway resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_legend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_legend`.
- Incoming transitions: runtime variable dispatch to room_legend; runtime
  variable dispatch to room_legend.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_legend_neo`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_legend_neo`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_library`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_ch2_scene8`,
  `obj_ch2_town_library`, `obj_doorW`, `obj_doorX`, `obj_mainchara`,
  `obj_markert`, `obj_markerw`, `obj_markerX`, `obj_npc_facing`, `obj_npc_room`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_lw_computer_lab`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch2_scene28b`, `obj_doorW`,
  `obj_mainchara`, `obj_markerw`, `obj_overworldc`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_lw_conbini`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorw_musfade`,
  `obj_mainchara`, `obj_markerv`, `obj_musicer_conbini`, `obj_npc_conbini`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_lw_icee_pizza`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch2_town_pizza`, `obj_doorW`,
  `obj_mainchara`, `obj_markert`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_lw_library_upstairs`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorW`, `obj_mainchara`, `obj_markert`,
  `obj_npc_library_upstairs`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdl_dark`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_lw_police`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_mainchara`, `obj_markerv`,
  `obj_npc_police`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_town_south.
- Conditions: No additional condition verified.

### Chapter 2: `room_musical_sync_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_musical_sync_test`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_school_unusedroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_unusedclassevent`.
- Incoming transitions: non-production unused classroom; excluded from ordered
  adjacency and only referenced by unused/fountain cleanup/readable-room
  compatibility code.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_schooldoor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_lw_cutscenes_short`, `obj_ch2_scene7`,
  `obj_darkdoor`, `obj_doorC`, `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_markerD`, `obj_markerX`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_schoollobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_ch2_lw_cutscenes_short`,
  `obj_ch2_room_schoollobby`, `obj_doorA`, `obj_doorAny`, `obj_doorB`,
  `obj_doorC`, `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerD`,
  `obj_markerX`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_sul`.
- Incoming transitions: door from room_town_school; enabled placed obj_doorA
  from room_torielclass resolves room_goto_next via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_town_school.
- Conditions: doorFadeMusic = global.plot < 200;.

### Chapter 2: `room_shaun_puzzle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorA`, `obj_doorB`,
  `obj_mainchara`, `obj_shapepuzzle`, `obj_shapepuzzlebutton`, `obj_soliddark`.
- Incoming transitions: placed obj_doorA/obj_doorB and obj_shapepuzzle drive
  ordered puzzle route.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_shop_ch2_music`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop_ch2_music`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_shop_ch2_spamton`

- Area: Cyber City.
- Runtime role/status: optional Spamton shop interface; verified production
  reachable.
- Important controllers: `obj_shop_ch2_spamton`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_shop_ch2_swatch`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop_ch2_swatch`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_shop1`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop1`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_sound_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_soundtester`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_sprite_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_spritecomparer`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_teacup_demoauto`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`, `obj_teacup`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_teacup_demobullets`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`, `obj_teacup`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_title_placeholder`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_doorB_musfade`, `obj_doorW`, `obj_markerA`,
  `obj_markerv`, `obj_soliddark`, `obj_title_placeholder`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 2: `room_torbathroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene31`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_sul`, `obj_sur`, `obj_town_event`.
- Incoming transitions: enabled placed obj_doorA from room_torhouse resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_torhouse`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_scene30b`, `obj_ch2_scene32`, `obj_doorA`,
  `obj_doorD`, `obj_doorX_musfade`, `obj_event_room`, `obj_mainchara`,
  `obj_markerB`, `obj_markerC`, `obj_markerX`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdl`, `obj_sdr`, `obj_solidblock`, `obj_solidlong`,
  `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorB from room_torbathroom resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_torielclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_mainchara`,
  `obj_markerB`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_torielclass_event`.
- Incoming transitions: enabled placed obj_doorB from room_schoollobby resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_torroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_apartments`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_church`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_event`, `obj_doorA`, `obj_doorC_musfade`,
  `obj_doorD`, `obj_doorX`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerD`, `obj_markerX`, `obj_musicer_town`, `obj_npc_room`,
  `obj_npc_room_animated`, `obj_overworldc`, `obj_sdl`, `obj_sdr`,
  `obj_solidblock`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_graveyard resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_krisyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_lw_cutscenes_short`, `obj_ch2_scene30a`,
  `obj_doorC`, `obj_doorX_musfade`, `obj_mainchara`, `obj_markerD`,
  `obj_markerX`, `obj_musicer_town`, `obj_npc_sign`, `obj_overworldc`,
  `obj_sdl`, `obj_sdr`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_mid`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_ch2_room_town_mid_diner`,
  `obj_doorC`, `obj_doorD`, `obj_doorW`, `obj_doorw_musfade`, `obj_doorX`,
  `obj_mainchara`, `obj_markerC`, `obj_markerD`, `obj_markert`, `obj_markerv`,
  `obj_markerw`, `obj_markerX`, `obj_musicer_town`, `obj_npc_room`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_town_event`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_north`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_town_north`, `obj_doorA`, `obj_doorC`,
  `obj_doorD`, `obj_doorX`, `obj_flowerking`, `obj_mainchara`, `obj_markerB`,
  `obj_markerC`, `obj_markerD`, `obj_markerX`, `obj_musicer_town`,
  `obj_npc_facing`, `obj_npc_room`, `obj_npc_sign`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorB from room_beach resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_northwest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_school`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_doorAny`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerX`, `obj_musicer_town`, `obj_overworldc`, `obj_sdr`,
  `obj_solidblock`.
- Incoming transitions: door from room_schoollobby; enabled placed obj_doorA
  from room_town_south resolves room_goto_next via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_schoollobby.
- Conditions: doorFadeMusic = global.plot < 200;.

### Chapter 2: `room_town_shelter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch2_room_town_shelter`, `obj_doorD_musfade`,
  `obj_mainchara`, `obj_markerC`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdl`, `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`,
  `obj_town_shelter_event`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_town_south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_ch2_room_town_south`,
  `obj_ch2_room_town_south_alphys`, `obj_ch2_scene29`, `obj_doorA`, `obj_doorC`,
  `obj_doorD`, `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markerB`,
  `obj_markerC`, `obj_markerD`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_town`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_sul`, `obj_town_event`.
- Incoming transitions: door from room_lw_police; enabled placed obj_doorB from
  room_town_school resolves room_goto_previous via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_townhall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_room`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdl`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 2: `room_transformation_sequence`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_anime_bg_controller`,
  `obj_thrash_transformation_controller`, `obj_thrash_transformation_original`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

## Chapter 3 (246 assets)

### Chapter 3: `PLACE_CONTACT`

- Area: Player flow.
- Runtime role/status: contact or chapter-entry runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_CONTACT_old`.
- Incoming transitions: runtime dispatch; runtime variable dispatch to
  PLACE_CONTACT.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `PLACE_DOG`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `PROCESS_DOG`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 3: `PLACE_DOGCHECK2`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_dogcheck2`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 3: `PLACE_FAILURE`

- Area: Player flow.
- Runtime role/status: failure/game-over runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_FAILURE`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `PLACE_LOGO`

- Area: Player flow.
- Runtime role/status: logo transition destination; verified production
  reachable.
- Important controllers: `PROCESS_LOGO`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `PLACE_MENU`

- Area: Player flow.
- Runtime role/status: title/menu runtime destination; verified production
  reachable.
- Important controllers: `DEVICE_MENU`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `PLACE_NAMING_JIKKEN`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `DEVICE_NAMER`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 3: `room_adventureboardtest`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_board_cactus_test`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_hazard`, `obj_board_solid`,
  `obj_board_specialwarp`, `obj_board_swordroute_loop_counter`,
  `obj_board_warpdoor`, `obj_board_warpentrance`, `obj_ch3_gameshow`,
  `obj_chaseenemy_board_spawner`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_mainchara_board`, `obj_pushableblock_board`, `obj_pushableblock_spawner`,
  `obj_quizchaser_spawner`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_alphysalley`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorW`, `obj_mainchara`, `obj_markerw`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_alphysclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_alphysdesk`, `obj_classscene`, `obj_mainchara`,
  `obj_markerA`, `obj_overworldc`, `obj_readable_room1`, `obj_schooldesk`,
  `obj_solidblock`, `obj_tem_school`.
- Incoming transitions: enabled placed obj_doorA from room_schoollobby resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_battletest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_battletester`, `obj_chaseenemy`,
  `obj_darkcontroller`, `obj_debugload`, `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch; debug/test runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 3: `room_beach`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_npc_room`, `obj_npc_sign`, `obj_onion_event`, `obj_overworldc`,
  `obj_room_beach`, `obj_solidblock`, `obj_wave_fx`.
- Incoming transitions: enabled placed obj_doorA from room_town_north resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_1`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b1_finale`, `obj_b1_finaledoor`,
  `obj_b1_finalehalls`, `obj_b1bonuszone`, `obj_b1cactusfield1`,
  `obj_b1cactusfield2`, `obj_b1controls`, `obj_b1enemy`, `obj_b1intro`,
  `obj_b1keyhint`, `obj_b1lancer`, `obj_b1mailroom`, `obj_b1mailroom_intro`,
  `obj_b1oasis`, `obj_b1power`, `obj_b1push2`, `obj_b1pushpyramid`,
  `obj_b1pyramid_rouxlsjoke`, `obj_b1pyramid1`, `obj_b1pyramid2`, `obj_b1quiz`,
  `obj_b1rocks1`, `obj_b1rockstrigger`, `obj_b1sphinx`, `obj_b1spring`,
  `obj_b1store`, `obj_b1susiedig`, `obj_b1swordconnector`,
  `obj_board_b1powerpond`, `obj_board_cactus`, `obj_board_cactus_flirt`,
  `obj_board_cactusmanager`, `obj_board_camera`, `obj_board_checkpoint`,
  `obj_board_controller`, `obj_board_event_bigdoor`, `obj_board_event_ninfight`,
  `obj_board_event_push1_blocktrigger`, `obj_board_event_push2_blocktrigger`,
  `obj_board_event_sphinx_tenna`, `obj_board_grabbablegrassspawner`,
  `obj_board_grabbleObject`, `obj_board_lancercactus`, `obj_board_lancermoat`,
  `obj_board_lancerswitch`, `obj_board_maildoor`, `obj_board_npc`,
  `obj_board_oasis`, `obj_board_pickup`, `obj_board_pointsGet`,
  `obj_board_smallpond`, `obj_board_softsolid`, `obj_board_solid`,
  `obj_board_solidenemy`, `obj_board_susiedig_groundspots`,
  `obj_board_treasuremarker`, `obj_board_treespawner`, `obj_board_trigger`,
  `obj_board_warpentrance`, `obj_board_warptouch`, `obj_board_waterfall`,
  `obj_bpush1`, `obj_bpush2_stucktrigger`, `obj_bpush2_stucktrigger_alt`,
  `obj_ch3_gameshow`, `obj_chaseenemy_board_spawner`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_mainchara_board`, `obj_pushableblock_board`,
  `obj_quizchaser_spawner`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_1_sword`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_1_sword_b1store`,
  `obj_board_1_sword_manager`, `obj_board_1_sword_shadowtease`,
  `obj_board_b1_shadowteaseentrance`, `obj_board_b1powerpond`,
  `obj_board_b1swordentrance`, `obj_board_cactus`, `obj_board_camera`,
  `obj_board_cold`, `obj_board_controller`, `obj_board_enemy_spawner`,
  `obj_board_fern`, `obj_board_lancermoat_sword`, `obj_board_oasis_sword`,
  `obj_board_pickup`, `obj_board_screenColorChanger`,
  `obj_board_smallpond_sword`, `obj_board_solid`, `obj_board_solidfish`,
  `obj_board_sword_fakeentrance`, `obj_board_sword_shadowtease_face`,
  `obj_board_sword_shadowtease_teeth`, `obj_board_swordroute_treeteleportroom`,
  `obj_board_treespawner`, `obj_board_trigger`, `obj_board_warpentrance`,
  `obj_board_warptouch`, `obj_board_waterfall`, `obj_darkcontroller`,
  `obj_gameshow_swordroute`, `obj_mainchara`, `obj_mainchara_board`.
- Incoming transitions: obj_gameshow_swordroute and obj_board_controller select
  and initialize sword-route board 1.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_1_sword_trees`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_board_screenColorChanger`, `obj_board_swordroute_treeteleportroom`,
  `obj_darkcontroller`, `obj_gameshow_swordroute`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: obj_gameshow_swordroute explicitly branches on
  room_board_1_sword_trees.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_2`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b2_antlionroom`, `obj_b2_badbridge`,
  `obj_b2_bino_v2`, `obj_b2_crabroom`, `obj_b2_ice_a1`, `obj_b2_ice_a2`,
  `obj_b2_ice_b1`, `obj_b2_ice_b2`, `obj_b2_ice_c1`, `obj_b2_ice_c2`,
  `obj_b2_ice_d1`, `obj_b2_ice_d2`, `obj_b2_ice_e1`, `obj_b2_ice_e2`,
  `obj_b2_moneyhole`, `obj_b2_photocactus`, `obj_b2_southwaterarea`,
  `obj_b2atlantis`, `obj_b2atlantisentrance`, `obj_b2atlantispreview`,
  `obj_b2bombfun`, `obj_b2bombfun2`, `obj_b2bombfunswitch`,
  `obj_b2bossencounterroom`, `obj_b2bridgeintro`, `obj_b2bridgepuzzle1`,
  `obj_b2bridgepuzzle2_alt`, `obj_b2camera`, `obj_b2d_centertrigger`,
  `obj_b2danger1`, `obj_b2enemy1`, `obj_b2enemysquabble`,
  `obj_b2enrichmentenclosure`, `obj_b2fashionshop1`, `obj_b2fashionshop2`,
  `obj_b2ferntalk`, `obj_b2heartisland`, `obj_b2iceregion`, `obj_b2intro`,
  `obj_b2lancersalsa`, `obj_b2loverbridge`, `obj_b2loverscliff`,
  `obj_b2lovershallway`, `obj_b2mowdock`, `obj_b2ninfriendotop`,
  `obj_b2northcross`, `obj_b2pantheonentrance`, `obj_b2photohint`,
  `obj_b2pippinsisland`, `obj_b2pippinsislandnpc`, `obj_b2pyramidrouxlsstore`,
  `obj_b2quiz2`, `obj_b2raftget`, `obj_b2raftintro`, `obj_b2ralseichoose`,
  `obj_b2riversouth`, `obj_b2sadislandprev`, `obj_b2savelancer`,
  `obj_b2southwest`, `obj_b2tennaleave1`, `obj_b2waterfall`, `obj_b2westpip`,
  `obj_b2westshop`, `obj_board_b2_atlantisdecor`, `obj_board_b2_boatwarp`,
  `obj_board_b2_bridgeoverlay`, `obj_board_b2_photopodium`,
  `obj_board_b2cameraglow`, `obj_board_b2drawbridge`,
  `obj_board_b2entrance_animatecamera`, `obj_board_b2entrance_animateonsen`,
  `obj_board_b2sword_boatwarp`, `obj_board_b2tornflower`, `obj_board_boat`,
  `obj_board_boatsolid`, `obj_board_breakableblockspawner`,
  `obj_board_bridgespawner`, `obj_board_camera`, `obj_board_camsolid`,
  `obj_board_cautiontape`, `obj_board_checkpoint`, `obj_board_controller`,
  `obj_board_dock`, `obj_board_dugtile`, `obj_board_enemySpawnLocation`,
  `obj_board_event_bridgepuzzle`, `obj_board_event_lawnmower`, `obj_board_fern`,
  `obj_board_grabbablegrass`, `obj_board_grabbablegrassspawner`,
  `obj_board_ladder`, `obj_board_lawnmower`, `obj_board_nothrow`,
  `obj_board_npc`, `obj_board_overlookfriendo`, `obj_board_pickup`,
  `obj_board_pointsGet`, `obj_board_resettile`, `obj_board_sadfriendo`,
  `obj_board_shadowgunner_spawn`, `obj_board_shallowwater`, `obj_board_solid`,
  `obj_board_solid_treegreen`, `obj_board_solidcorner`, `obj_board_solidenemy`,
  `obj_board_solvedtrigger`, `obj_board_tree_grayscale`, `obj_board_trigger`,
  `obj_board_warptouch`, `obj_board_waterfall`, `obj_board_watertile`,
  `obj_board_weedmow`, `obj_ch3_gameshow`, `obj_chaseenemy_board_spawner`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_mainchara_board`.
- Incoming transitions: board minigame control flow reaches board 2;
  obj_board_controller and board death/game-over code explicitly handle it.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_2_sword`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b2s_heartisland`, `obj_b2s_northernlightsroom`,
  `obj_b2s_swordmanager`, `obj_b2s_swordroom`, `obj_b2s_tennaentrance`,
  `obj_b2s_tennamonologue`, `obj_board_b2_bridgeoverlay`,
  `obj_board_b2s_icedoor`, `obj_board_b2sword_boatwarp`, `obj_board_boat`,
  `obj_board_boatsolid`, `obj_board_bridgespawner`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_dock`, `obj_board_enemy_spawner`,
  `obj_board_fern`, `obj_board_ladder`, `obj_board_pickup`,
  `obj_board_screenColorChanger`, `obj_board_shallowwater`, `obj_board_solid`,
  `obj_board_solid_treegreen`, `obj_board_solidfish`,
  `obj_board_tree_grayscale`, `obj_board_trigger`, `obj_board_warptouch`,
  `obj_board_waterfall`, `obj_darkcontroller`, `obj_gameshow_swordroute`,
  `obj_mainchara`, `obj_mainchara_board`.
- Incoming transitions: obj_gameshow_swordroute explicitly selects and
  initializes sword-route board 2.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_3`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b2iceregion`, `obj_b3_tennablossom`,
  `obj_b3alley`, `obj_b3bridge`, `obj_b3cactusfield`, `obj_b3cactusflirt`,
  `obj_b3camerashop`, `obj_b3center`, `obj_b3danger1`, `obj_b3danger2`,
  `obj_b3desert`, `obj_b3dock1`, `obj_b3dock2`, `obj_b3elevator`,
  `obj_b3encountera`, `obj_b3entertainmentalley`, `obj_b3entertainmentdistrict`,
  `obj_b3gameshow`, `obj_b3gameshow_tvseq`, `obj_b3grassjoke`, `obj_b3intro`,
  `obj_b3lobby`, `obj_b3quiza`, `obj_b3quizb`, `obj_b3stairs`,
  `obj_b3underground`, `obj_b3undergroundleft`, `obj_b3undergroundright`,
  `obj_board_b3_elevatorcheck`, `obj_board_b3topdoor`,
  `obj_board_b3undergroundright_warpdoor`, `obj_board_boat`,
  `obj_board_boatsolid`, `obj_board_cactus`, `obj_board_camera`,
  `obj_board_checkpoint`, `obj_board_controller`, `obj_board_dock`,
  `obj_board_grabbablegrassspawner`, `obj_board_npc`, `obj_board_solid`,
  `obj_board_solidcorner`, `obj_board_trigger`, `obj_board_warptouch`,
  `obj_ch3_gameshow`, `obj_chaseenemy_board_spawner`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_mainchara_board`, `obj_quizchaser_spawner`.
- Incoming transitions: board minigame control flow reaches board 3;
  obj_board_controller and board death/game-over code explicitly handle it.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_3_sword`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3s_swordmanager`, `obj_board_b3s_stanchion`,
  `obj_board_cactus`, `obj_board_camera`, `obj_board_controller`,
  `obj_board_pickup`, `obj_board_screenColorChanger`, `obj_board_solid`,
  `obj_board_solidcorner`, `obj_board_trigger`, `obj_board_warptouch`,
  `obj_darkcontroller`, `obj_gameshow_swordroute`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: obj_gameshow_swordroute explicitly selects and
  initializes sword-route board 3.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_3b`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3belevator`, `obj_b3belevatorroom`,
  `obj_b3bfinale`, `obj_b3bintro`, `obj_board_aimoverwrite`,
  `obj_board_b3b_elevatorbg`, `obj_board_camera`, `obj_board_controller`,
  `obj_board_grabbleObject`, `obj_board_solid`, `obj_board_solidcorner`,
  `obj_board_trigger`, `obj_ch3_gameshow`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_mainchara_board`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_boattest`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_board_boat`, `obj_board_boatsolid`,
  `obj_board_camera`, `obj_board_controller`, `obj_board_dock`,
  `obj_board_event_lawnmower`, `obj_board_lawnmower`, `obj_board_npc`,
  `obj_board_solid`, `obj_board_solidenemy`, `obj_board_weedmow`,
  `obj_ch3_gameshow`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_designTest`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_board_basicSpace`, `obj_board_camera`,
  `obj_board_camerashifter`, `obj_board_check_warp`, `obj_board_controller`,
  `obj_board_dodgetile`, `obj_board_enemy_flower`,
  `obj_board_enemy_pricklycactus`, `obj_board_freeroam_warp_touch`,
  `obj_board_npc`, `obj_board_pointsAdd_OLD`, `obj_board_quiztile`,
  `obj_board_solid`, `obj_ch3_gameshow`, `obj_darkcontroller`, `obj_event_npc`,
  `obj_mainchara`, `obj_mainchara_board`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_dungeon_2`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b2d_centertrigger`, `obj_b2d_dungeoncorner`,
  `obj_b2d_dungeonend`, `obj_b2d_firstencounter`, `obj_b2d_firstswitches`,
  `obj_b2d_icedoor`, `obj_b2d_intro`, `obj_b2d_mazeescape`,
  `obj_b2d_mazemanager`, `obj_b2d_threefreeze`, `obj_b2d_treefreeze`,
  `obj_board_camera`, `obj_board_controller`,
  `obj_board_dungeon_2_jingle_controller`, `obj_board_dungeon_2_roomWriter`,
  `obj_board_dungeon_2_roomWriterManager`, `obj_board_enemy_spawner`,
  `obj_board_glacier_switch3`, `obj_board_mazewater1`, `obj_board_mazewater2`,
  `obj_board_mazewater3`, `obj_board_mazewater4`,
  `obj_board_screenColorChanger`, `obj_board_solid`, `obj_board_solid_monster`,
  `obj_board_solidenemy`, `obj_board_treespawner`, `obj_board_warptouch`,
  `obj_darkcontroller`, `obj_gameshow_swordroute`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_dungeon_3`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_b3s_repeatintro`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_dungeon_3_jingle_controller`,
  `obj_board_dungeon_3_shelter`, `obj_board_dungeon3_sheltertunnel`,
  `obj_board_dungeon3_switch`, `obj_board_dungeon3_tenna`,
  `obj_board_enemy_spawner`, `obj_board_invincibilespot`,
  `obj_board_screenColorChanger`, `obj_board_solid`, `obj_board_treespawner`,
  `obj_board_warptopreshadowmantle`, `obj_darkcontroller`,
  `obj_dungeon3_tennataps`, `obj_gameshow_swordroute`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_empty`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_stage`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_interstitial; door from
  room_dw_b3bs_template; runtime dispatch.
- Outgoing transitions: to room_dw_b3bs_interstitial.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_gsa02_b0`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_ch3_gameshow`, `obj_darkcontroller`, `obj_GSA02_B0`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_intro`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b0entrance`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_event_intro1`, `obj_board_event_intro2`,
  `obj_board_solid`, `obj_board_trigger`, `obj_ch3_gameshow`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_mainchara_board`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_postshadowmantle`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_board_npc`, `obj_board_solid`, `obj_board_trigger`,
  `obj_bpush2_stucktrigger`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_gameshow_swordroute`, `obj_mainchara`, `obj_mainchara_board`,
  `obj_solidblocksized`, `obj_swordroute_event_leavescreen`,
  `obj_treasure_room`.
- Incoming transitions: obj_gameshow_swordroute explicitly handles the
  post-Shadow-Mantle route room.
- Outgoing transitions: to room_dw_console_room.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_postshadowmantle_test`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_darkcontroller`, `obj_gameshow_swordroute`, `obj_krisgrabsusietest`,
  `obj_mainchara`, `obj_mainchara_board`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_prepostshadowmantle`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_board_prepostshadowmantle`, `obj_board_smokepuff`, `obj_board_solid`,
  `obj_darkcontroller`, `obj_gameshow_swordroute`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: obj_gameshow_swordroute explicitly handles the pre/post
  Shadow-Mantle transition room.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_preshadowmantle`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_board_preshadowmantle`, `obj_board_shadowspotlight`, `obj_board_solid`,
  `obj_darkcontroller`, `obj_gameshow_swordroute`, `obj_mainchara`,
  `obj_mainchara_board`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_preshadowmantle_repeat`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_board_preshadowmantle`, `obj_board_preshadowmantle_repeat`,
  `obj_board_shadowspotlight`, `obj_board_solid`, `obj_darkcontroller`,
  `obj_gameshow_swordroute`, `obj_mainchara`, `obj_mainchara_board`.
- Incoming transitions: obj_gameshow_swordroute explicitly handles the repeat
  pre-Shadow-Mantle route room.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board_sword_intro`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; conditional.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_darkcontroller`, `obj_gameshow_swordroute`, `obj_mainchara`,
  `obj_mainchara_board`, `obj_markerAny`.
- Incoming transitions: door from room_dw_console_room; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: gates playable state with global.plot and global.flag\[1055\], and
  advances plot to 121.

### Chapter 3: `room_board_tests`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_b2savelancer`, `obj_board_breakableblockspawner`,
  `obj_board_bridgespawner`, `obj_board_cactus_test`, `obj_board_camera`,
  `obj_board_camsolid`, `obj_board_controller`, `obj_board_event_b2swap`,
  `obj_board_event_bridgepuzzle`, `obj_board_grabbablebomb`,
  `obj_board_grabbablegrass`, `obj_board_grabbablegrassspawner`,
  `obj_board_grabbleObject`, `obj_board_npc`, `obj_board_penaltyshot`,
  `obj_board_photoparent`, `obj_board_pickup`, `obj_board_solid`,
  `obj_board_solvedtrigger`, `obj_board_store_key`, `obj_board_treespawner`,
  `obj_board_trigger`, `obj_board_watertile`, `obj_ch3_gameshow`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_mainchara_board`,
  `obj_pushableblock_board`, `obj_quizchaser_spawner`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_board1_oldtest`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_board_basicSpace`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_dodgetile`, `obj_board_enemy_flower`,
  `obj_board_enemy_pricklycactus`, `obj_board_eventtile`,
  `obj_board_freeroam_warp_touch`, `obj_board_movingEnemy`, `obj_board_pptile`,
  `obj_board_quiztile`, `obj_board_solid`, `obj_board_touch_warp`,
  `obj_ch3_gameshow`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_mainchara_board`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_boardtest`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_board_basicSpace`, `obj_board_camera`,
  `obj_board_camerashifter`, `obj_board_controller`, `obj_board_dodgetile`,
  `obj_board_enemy_flower`, `obj_board_enemy_pricklycactus`,
  `obj_board_freeroam_warp_touch`, `obj_board_npc`, `obj_board_oasis_old`,
  `obj_board_quiztile`, `obj_board_solid`, `obj_board_touch_warp`,
  `obj_ch3_gameshow`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_mainchara_board`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_boardtest_old`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; uncertain-no-ingress.
- Important controllers: `obj_board_camera`, `obj_board_camerashifter`,
  `obj_board_check_warp`, `obj_board_controller`, `obj_board_dodgetile`,
  `obj_board_freeroam_warp_touch`, `obj_board_movingEnemy`,
  `obj_board_oasis_old`, `obj_board_readable`, `obj_board_solid`,
  `obj_board_touch_warp`, `obj_boardtile`, `obj_ch3_gameshow`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_mainchara_board`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_bullettest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_bullettester`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch; debug/test runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 3: `room_bullettest_new`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_bullettester_new`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 3: `room_castle_tutorial`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_tutorial`, `obj_darkcontroller`,
  `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markers`, `obj_markerw`,
  `obj_markerX`, `obj_musicer_darkcastle`, `obj_npc_room`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_cc_clover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorD_musfade`,
  `obj_mainchara`, `obj_markerC`, `obj_npc_room`, `obj_npc_room_animated`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_cc_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_darkfountain`, `obj_fountainkris`.
- Incoming transitions: runtime controller explicitly checks room_cc_fountain.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_cc_lancer`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bluhpainting`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_markerX`, `obj_npc_room`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_ch3_gacharoom_unknown`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_gachaunknown`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblock_32`, `obj_trigger_interact`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_ch3_gameshowroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_audience`, `obj_ch3_GSA02`, `obj_ch3_GSA06`,
  `obj_ch3_GSB01`, `obj_ch3_GSB03`, `obj_ch3_GSC07`, `obj_ch3_GSD01`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_gameshow_screen`,
  `obj_dw_gameshow_stage_overlay`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_tv_curtain; door from
  room_dw_tv_cutscene1g; runtime dispatch; runtime dispatch; runtime dispatch;
  runtime dispatch; runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_green_room.
- Conditions: No additional condition verified.

### Chapter 3: `room_ch3_gameshowroom_tennatest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch3_audience`, `obj_ch3_GSA02`, `obj_ch3_GSA06`,
  `obj_ch3_GSB03`, `obj_ch3_GSC07`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_green_room.
- Conditions: No additional condition verified.

### Chapter 3: `room_chapter_continue`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chapter_continue`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_CHEFS`

- Area: TV World.
- Runtime role/status: Chef minigame subsystem state/toggle room driven by
  obj_chefs_toggles and obj_chefs_game; verified production reachable.
- Important controllers: `obj_chefs_toggles`.
- Incoming transitions: chef minigame subsystem context runtime controller
  references room_CHEFS.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_cutscene_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_conveyorbelt`, `obj_cutscene_test`,
  `obj_darkcontroller`, `obj_forcefield`, `obj_heightfloor`,
  `obj_heightfloor_changer`, `obj_mainchara`, `obj_npc_room_animated`,
  `obj_npc_sign`, `obj_solidblocksized`, `obj_soliddark`, `obj_sticky_example`,
  `obj_swordobj_example`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_cutscene_tester_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_example_cutscene_b`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_DARKbase_GMS2`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 3: `room_DARKempty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 3: `room_debug_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_battle`, `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_battleBalloon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_ballooner`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_choicer_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_choicer`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_choicer_light`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_choicer`, `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_color`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_swatchling`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_loc`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_loc`, `obj_hallway_mirror`, `obj_mainchara`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_solidlong`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_smallface`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_smallfacetester`, `obj_mainchara`,
  `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_smallface_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_smallfacetester`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_debug_tennatexttester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_tennatexttester`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_diner`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_catti`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_sur`, `obj_town_diner`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_bibliox`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_bibliox`, `obj_b3bs_console`,
  `obj_board_camera`, `obj_board_controller`, `obj_board_solid`,
  `obj_board_solidcorner`, `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_extrapuzzle.
- Outgoing transitions: to room_dw_b3bs_extrapuzzle.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_camerareminder`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_solid`, `obj_board_treespawner`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_b3bs_camerareminder`,
  `obj_dw_ch3_b3bs_zapperhead`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_cheaterpippins.
- Outgoing transitions: to room_dw_b3bs_cheaterpippins.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_cheaterpippins`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_cheaterpippins`, `obj_b3bs_console`,
  `obj_board_camera`, `obj_board_controller`, `obj_board_nothrow`,
  `obj_board_solid`, `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_camerareminder; door from
  room_dw_b3bs_idcardpuzzle; door from room_dw_b3bs_watercooler.
- Outgoing transitions: to room_dw_b3bs_camerareminder; to
  room_dw_b3bs_idcardpuzzle; to room_dw_b3bs_watercooler.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_cooltrashy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_cooltrashy`, `obj_b3bs_stealth`,
  `obj_b3bs_stealtharea`, `obj_b3bs_stealthSolid`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`,
  `obj_treasure_room`.
- Incoming transitions: door from room_dw_b3bs_rabbick_b; door from
  room_dw_teevie_shadow_guys; door from room_dw_teevie_shadow_guys; door from
  room_dw_teevie_susiebridge.
- Outgoing transitions: to room_dw_teevie_shadow_guys; to
  room_dw_teevie_shadow_guys; to room_dw_teevie_susiebridge.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_extrapuzzle`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_fern`, `obj_board_solid`,
  `obj_board_solidenemy`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_b3bs_extrapuzzle`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_bibliox; door from
  room_dw_b3bs_zapper_d; runtime dispatch.
- Outgoing transitions: to room_dw_b3bs_bibliox; to room_dw_b3bs_zapper_d.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_idcardpuzzle`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_npc`, `obj_board_solid`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_b3bs_idcardpuzzle_pond`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_cheaterpippins.
- Outgoing transitions: to room_dw_b3bs_cheaterpippins.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_interstitial`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_interstitial_floor`,
  `obj_dw_teevie_statue`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_green_room`, `obj_room_interstitial`, `obj_solidblocksized`.
- Incoming transitions: door from room_board_empty; door from
  room_dw_b3bs_intro; door from room_dw_green_room; door from
  room_dw_green_room; runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_board_empty; to room_dw_b3bs_intro; to
  room_dw_green_room.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_intro`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_b3bs_introscene`,
  `obj_board_b3bs_intro`, `obj_board_bs_warp`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_solid`, `obj_board_treasuremarker`,
  `obj_ch3_GSA07`, `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_interstitial; door from
  room_dw_b3bs_zapper_a_old.
- Outgoing transitions: to room_dw_b3bs_interstitial; to room_dw_b3bs_jail1; to
  room_dw_b3bs_zapper_a.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_jail1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_b3bs_jail1`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`,
  `obj_shortcut_door`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_intro; door from
  room_dw_b3bs_zapper_a; door from room_dw_teevie_susiezilla.
- Outgoing transitions: to room_dw_b3bs_zapper_a; to room_dw_teevie_susiezilla.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_jail2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_jail2`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_watercooler; door from
  room_dw_teevie_cowboy_zone_02_intro; door from room_dw_teevie_ribbicks_b.
- Outgoing transitions: to room_dw_teevie_cowboy_zone_02_intro; to
  room_dw_teevie_ribbicks_b.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_lancerget`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_b3bs_lancerget`,
  `obj_board_camera`, `obj_board_controller`, `obj_board_solid`,
  `obj_board_treasuremarker`, `obj_board_trigger`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_shop; door from
  room_dw_teevie_large_01.
- Outgoing transitions: to room_dw_teevie_large_01.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_mysterypuzzle`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_fern`, `obj_board_resettile`,
  `obj_board_solid`, `obj_board_solidenemy`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_b3bs_mysterypuzzle`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_b3bs_shop; door from
  room_dw_teevie_large_02; runtime dispatch.
- Outgoing transitions: to room_dw_teevie_large_02.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_rabbick_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_rabbick_a`, `obj_b3bs_ribbick_trash`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw__backstagelight`,
  `obj_dw_b3bs_placeholdertrash`, `obj_dw_ch3_b3bs_trashcan`, `obj_mainchara`,
  `obj_markerAny`, `obj_npc_sign`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_shop.
- Outgoing transitions: to room_dw_b3bs_shop; to room_dw_b3bs_zapper_b.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_rabbick_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_b3bs_rabbick_b`, `obj_dw_ch3_b3bs_trashcan_interactor`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_sadshadowguys.
- Outgoing transitions: to room_dw_b3bs_cooltrashy; to
  room_dw_b3bs_sadshadowguys.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_rouxls_boss`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_GSC04C`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_rouxls_lanina.
- Outgoing transitions: to room_dw_b3bs_rouxls_lanina.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_rouxls_lanina`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_bridgespawner`,
  `obj_board_camera`, `obj_board_controller`, `obj_board_flowers`,
  `obj_board_resettile`, `obj_board_solid`, `obj_board_solvedtrigger`,
  `obj_board_treasuremarker`, `obj_ch3_GSC04B`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_b3bs_idcardpuzzle_pond`, `obj_dw_b3bs_rouxls_lanina`,
  `obj_dw_b3bs_rouxls_lanina_elninapondprogress`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_b3bs`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_rouxls_boss; door from
  room_dw_b3bs_sadshadowguys.
- Outgoing transitions: to room_dw_b3bs_rouxls_boss; to
  room_dw_b3bs_sadshadowguys.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_sadshadowguys`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_board_lawnmower`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_b3bs_sadshadowguys`,
  `obj_dw_ch3_b3bs_office_paperstack`, `obj_dw_ch3_b3bs_officesign`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_rabbick_b; door from
  room_dw_b3bs_rouxls_lanina; door from room_dw_b3bs_watercooler.
- Outgoing transitions: to room_dw_b3bs_rabbick_b; to
  room_dw_b3bs_rouxls_lanina; to room_dw_b3bs_watercooler.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_shop`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw__backstagelight`, `obj_mainchara`, `obj_markerAny`,
  `obj_room_backstage_shop`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_rabbick_a; door from
  room_dw_b3bs_zapper_a_old.
- Outgoing transitions: to room_dw_b3bs_lancerget; to
  room_dw_b3bs_mysterypuzzle; to room_dw_b3bs_rabbick_a; to
  room_dw_b3bs_zapper_a.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_template`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_board_empty.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_watercooler`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_stealtharea`, `obj_b3bs_stealthSolid`,
  `obj_b3bs_watercooler`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_b3bs_trashcan`, `obj_dw_ch3_b3bs_zapperhead`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_b3bs`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_cheaterpippins; door from
  room_dw_b3bs_sadshadowguys; door from room_dw_b3bs_zapper_a_old.
- Outgoing transitions: to room_dw_b3bs_cheaterpippins; to room_dw_b3bs_jail2;
  to room_dw_b3bs_sadshadowguys; to room_dw_b3bs_zapper_a; to
  room_dw_b3bs_zapper_c.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_zapper_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_stealth`, `obj_b3bs_stealtharea`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_b3bs_zapper_a`,
  `obj_dw_ch3_b3bs_zappera_trashswitch`, `obj_dw_ch3_b3bs_zapperhead`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_intro; door from
  room_dw_b3bs_jail1; door from room_dw_b3bs_shop; door from
  room_dw_b3bs_watercooler; door from room_dw_teevie_ribbicks_a.
- Outgoing transitions: to room_dw_b3bs_jail1; to room_dw_teevie_ribbicks_a.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_zapper_a_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy_zapper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw__backstagelight`, `obj_dw_b3bs_zapper_a`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_b3bs_intro; to room_dw_b3bs_shop; to
  room_dw_b3bs_watercooler.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_zapper_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_stealtharea`, `obj_b3bs_stealthSolid`,
  `obj_b3bs_zapper_b`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_b3bs_zapperhead`, `obj_dw_teevie_zapperbtimeout`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_rabbick_a; door from
  room_dw_teevie_ribbicks_a; door from room_dw_teevie_ribbicks_b; door from
  room_dw_teevie_watercooler.
- Outgoing transitions: to room_dw_teevie_ribbicks_a; to
  room_dw_teevie_ribbicks_b; to room_dw_teevie_watercooler.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_zapper_c`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_stealtharea`, `obj_b3bs_zapper_c`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_ch3_b3bs_zapperhead`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`, `obj_solidblocksized`,
  `obj_treasure_room`.
- Incoming transitions: door from room_dw_b3bs_watercooler; door from
  room_dw_teevie_dust_south.
- Outgoing transitions: to room_dw_teevie_dust_south.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bs_zapper_d`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_zapper_d`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_extrapuzzle.
- Outgoing transitions: to room_dw_b3bs_extrapuzzle.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_b3bstest`

- Area: Development.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; debug-test.
- Important controllers: `obj_b3bs_console`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_grabbleObject`, `obj_board_lawnmower`,
  `obj_board_solid`, `obj_board_solidenemy`, `obj_board_tree`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: debug/test door from room_dw_b3bstest_big.
- Outgoing transitions: to room_dw_b3bstest_big.
- Conditions: debug input.

### Chapter 3: `room_dw_b3bstest_big`

- Area: Development.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; debug-test.
- Important controllers: `obj_b3bs_bigtest`, `obj_b3bs_console`,
  `obj_board_camera`, `obj_board_controller`, `obj_board_resetbell`,
  `obj_board_solid`, `obj_board_treespawner`, `obj_board_trigger`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_pushableblock_spawner`, `obj_solidblocksized`.
- Incoming transitions: debug/test door from room_dw_b3bstest.
- Outgoing transitions: to room_dw_b3bstest.
- Conditions: debug input.

### Chapter 3: `room_dw_backstage`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_GSD02`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_intro; runtime dispatch.
- Outgoing transitions: to room_dw_teevie_intro.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_area_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_dw_leave`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_room_castle_area_1`,
  `obj_sdl_dark`, `obj_sdr_dark`, `obj_soliddark`, `obj_sul_dark`,
  `obj_sur_dark`.
- Incoming transitions: enabled placed obj_doorB from
  room_dw_ralsei_castle_front resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_cafe`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_cafe`, `obj_npc_castle_cafe`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_dojo`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_dojo_allstarsPlaylist`, `obj_darkcontroller`,
  `obj_dojofx`, `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_readable_room1`, `obj_room_castle_dojo`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_dungeon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_king`, `obj_room_dungeon_2f`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_east_door`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_castle_door`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_restaurant`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_castle_bakery`, `obj_sdl`, `obj_sdr`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_rooms_kris`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerv`, `obj_readable_room1`, `obj_room_castle_kris`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_rooms_susie`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_readable_room1`, `obj_room_castle_susie`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_town`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_castle_cafe`,
  `obj_castle_dojo`, `obj_castle_house`, `obj_castle_restaurant`,
  `obj_castle_shop`, `obj_castle_torch`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorX`, `obj_doorX_musfade`, `obj_mainchara`, `obj_markerB`,
  `obj_markerr`, `obj_markers`, `obj_markert`, `obj_markeru`, `obj_markerv`,
  `obj_markerw`, `obj_markerX`, `obj_musicer_darkcastle`, `obj_npc_room`,
  `obj_readable_room1`, `obj_room_castle_town`, `obj_savepoint`, `obj_sdl_dark`,
  `obj_sdr_dark`, `obj_soliddark`, `obj_sul`, `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_castle_west_cliff`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darklanding`, `obj_doorX`,
  `obj_mainchara`, `obj_markerD`, `obj_markerX`, `obj_npc_castle_cliff`,
  `obj_npc_room`, `obj_soliddark`, `obj_treasure_room`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ch3_man`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_dmg`, `obj_ch3_man_controller`,
  `obj_ch3_man_warp`, `obj_darkcontroller`, `obj_mainchara`, `obj_musicer_gen`,
  `obj_npc_room`, `obj_solidblock_32`, `obj_solidblock_diagonal_32`,
  `obj_triggervolume`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_changing_room`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_changing_room_curtain`, `obj_dw_changing_room_stars`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_changing_room`, `obj_room_changing_room`,
  `obj_solidblocksized`, `obj_solidblocksized_alt`.
- Incoming transitions: door from room_dw_console_room; door from
  room_dw_inbetween; door from room_dw_inbetweenhall.
- Outgoing transitions: to room_dw_console_room; to room_dw_inbetween; to
  room_dw_inbetweenhall.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_channelchange_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_actor_tenna`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_screen_channel_change`,
  `obj_screen_channel_change_sprite_test`, `obj_screen_channel_change_tester`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_chef`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_GSA04`, `obj_darkcontroller`,
  `obj_dw_chef_screen`, `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_chef_empty`

- Area: TV World.
- Runtime role/status: Chef-show empty-stage presentation driven by
  obj_room_chef_empty and screen controllers; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dw_chef_screen`,
  `obj_dw_chef_screen_empty`, `obj_mainchara`, `obj_room_chef_empty`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_console_room`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_console_room`, `obj_solidblocksized`.
- Incoming transitions: door from room_board_postshadowmantle; door from
  room_dw_changing_room; runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_board_sword_intro; to room_dw_changing_room.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_overworld_01`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_couch_overworld_controller`, `obj_ch3_PGS01B`,
  `obj_circlezoom`, `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorAny`,
  `obj_dustpile`, `obj_dw_couch_bg_parallax`, `obj_dw_wobbler`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_02; door from
  room_dw_couch_overworld_intro.
- Outgoing transitions: to room_dw_couch_overworld_02; to
  room_dw_couch_overworld_intro.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_overworld_02`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_PGS01B_convo`, `obj_ch3_PGS01B_eyepuzzle`,
  `obj_ch3_PGS01B_eyepuzzle_switch`, `obj_circlezoom`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_doorAny`, `obj_dustpile`, `obj_dw_rabbick_outline`,
  `obj_dw_wobbler`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_01; door from
  room_dw_couch_overworld_03; door from room_dw_couch_points.
- Outgoing transitions: to room_dw_couch_overworld_01; to
  room_dw_couch_overworld_03; to room_dw_couch_points.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_overworld_03`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_area`,
  `obj_ch3_couch_overworld_controller`, `obj_ch3_PGS01B_convo`,
  `obj_circlezoom`, `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorAny`,
  `obj_dustpile`, `obj_dw_couch_bg_parallax`, `obj_dw_rabbick_outline`,
  `obj_dw_wobbler`, `obj_glowtile`, `obj_glowtilepuzz`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_02; door from
  room_dw_couch_overworld_04.
- Outgoing transitions: to room_dw_couch_overworld_02; to
  room_dw_couch_overworld_04.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_overworld_04`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_PGS01B_convo`, `obj_circlezoom`,
  `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorAny`,
  `obj_dw_shutta_hand`, `obj_dw_wobbler`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_03; door from
  room_dw_couch_overworld_05.
- Outgoing transitions: to room_dw_couch_overworld_03; to
  room_dw_couch_overworld_05.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_overworld_05`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_PGS01B_convo`, `obj_ch3_PGS01C`,
  `obj_ch3_PGS01F`, `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_04; runtime dispatch.
- Outgoing transitions: to room_dw_couch_overworld_04.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_overworld_intro`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch3_PGS01A`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_couch_bg_parallax`, `obj_mainchara`, `obj_markerAny`, `obj_savepoint`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_01; door from
  room_dw_couch_overworld_intro_left; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_couch_overworld_01; to
  room_dw_couch_overworld_intro_left.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_overworld_intro_left`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_couch_overworld_controller`, `obj_circlezoom`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_intro.
- Outgoing transitions: to room_dw_couch_overworld_intro.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_points`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_couch_overworld_controller`, `obj_circlezoom`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dustpile`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_couch_overworld_02.
- Outgoing transitions: to room_dw_couch_overworld_02.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_couch_video`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_couch_video`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_green_room`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_green_room_racing`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_green_room_bg_fx`, `obj_dw_green_room_tile_fx`,
  `obj_dw_green_room_vines`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_green_room`, `obj_room_green_room`, `obj_solidblock_32`,
  `obj_solidblocksized`, `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: door from room_ch3_gameshowroom; door from
  room_dw_b3bs_interstitial; door from room_dw_inbetween; door from
  room_dw_inbetweenhall; door from room_dw_inbetweenhall; door from
  room_dw_puzzlecloset_0; door from room_dw_puzzlecloset_3; door from
  room_dw_ranking_hub; door from room_dw_teevie_preview; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_b3bs_interstitial; to
  room_dw_b3bs_interstitial; to room_dw_puzzlecloset_0; to room_dw_ranking_hub;
  to room_dw_teevie_preview.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_inbetween`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_inbetween_room_bg_fx`, `obj_dw_inbetween_room_vines`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_room_inbetween`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_changing_room; runtime dispatch.
- Outgoing transitions: to room_dw_changing_room; to room_dw_green_room.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_inbetweenhall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ranking_hub_floor`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_changing_room; runtime dispatch.
- Outgoing transitions: to room_dw_changing_room; to room_dw_green_room; to
  room_dw_green_room; to room_dw_ranking_z_hallway.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_nondescript_classroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_PGS01E_classroom`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_nondescript_field`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_ch3_PGS01E_field`,
  `obj_purplegrass`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_nondescript_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_PGS01E_hallway`, `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_nondescript_room`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_PGS01D`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_puzzlecloset_0`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_puzzlecloset0_introsequence`, `obj_dw_ch3_puzzleclosetbg_effect`,
  `obj_dw_ch3_tvsnow`, `obj_mainchara`, `obj_markerAny`,
  `obj_puzzlecloset_manager`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_green_room; door from
  room_dw_puzzlecloset_1.
- Outgoing transitions: to room_dw_green_room; to room_dw_puzzlecloset_1.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_puzzlecloset_1`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_grabbablegrass`, `obj_board_solid`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_ch3_puzzleclosetbg_effect`,
  `obj_dw_puzzlecloset_1_consolesequence`, `obj_dw_puzzlecloset_1_solidarea`,
  `obj_dw_puzzlecloset_dooriel`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_pushableblock_board`, `obj_puzzlecloset_manager`,
  `obj_solidblock_diagonal_32`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_puzzlecloset_0; door from
  room_dw_puzzlecloset_1a.
- Outgoing transitions: to room_dw_puzzlecloset_0; to room_dw_puzzlecloset_1a.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_puzzlecloset_1a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_puzzleclosetbg_effect`, `obj_dw_ch3_tvsnow`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_puzzle_closet_1a`, `obj_solidblock_32`,
  `obj_solidblock_diagonal_32`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_puzzlecloset_1; door from
  room_dw_puzzlecloset_2.
- Outgoing transitions: to room_dw_puzzlecloset_1; to room_dw_puzzlecloset_2.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_puzzlecloset_2`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_chasekey`, `obj_b3bs_console`,
  `obj_b3bs_pointobj`, `obj_board_aimoverwrite`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_pc2_sworddoor`, `obj_board_solid`,
  `obj_board_trigger`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_puzzleclosetbg_effect`, `obj_dw_puzzlecloset_1_bush`,
  `obj_dw_puzzlecloset_2_glowmanager`, `obj_dw_puzzlecloset_dooriel`,
  `obj_dw_puzzlecloset_warp`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_puzzlecloset_manager`, `obj_solidblock_diagonal_32`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_puzzlecloset_1a; door from
  room_dw_snow_zone.
- Outgoing transitions: to room_dw_puzzlecloset_1a; to room_dw_snow_zone.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_puzzlecloset_3`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_bridgespawner`,
  `obj_board_camera`, `obj_board_camsolid`, `obj_board_controller`,
  `obj_board_nothrow`, `obj_board_pickup`, `obj_board_resettile`,
  `obj_board_solid`, `obj_board_solidcorner`, `obj_board_solidenemy`,
  `obj_board_solvedtrigger`, `obj_board_trigger`, `obj_board_tvinteract`,
  `obj_board_warptouch`, `obj_board_watertile`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_ch3_puzzleclosetbg_effect`,
  `obj_dw_puzzlecloset_dooriel`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_pc3_room1`, `obj_pc3_room2`,
  `obj_puzzlecloset_manager`, `obj_puzzlecloset3_hallway_mirror`,
  `obj_solidblock_diagonal_32`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_green_room; to room_dw_snow_zone.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ralsei_castle_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_cauldron_glow`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorW`, `obj_mainchara`, `obj_markerB`, `obj_markerw`,
  `obj_markerX`, `obj_npc_room_animated`, `obj_readable_room1`,
  `obj_room_castle_1f`, `obj_room_castle_1f_cake`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_ralsei_castle_2f
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ralsei_castle_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorB`, `obj_doorW`,
  `obj_mainchara`, `obj_markerA`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_readable_room1`, `obj_room_castle_2f`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_ralsei_castle_1f
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ralsei_castle_front`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_torch`, `obj_darkcontroller`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerX`, `obj_npc_room`,
  `obj_npc_room_animated`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ranking_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_blue_starry_wall`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_room_ranking_a`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_ranking_hub; runtime dispatch; runtime
  dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_ranking_hub.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ranking_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_ranking_b_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_ranking_b`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_ranking_hub; runtime dispatch.
- Outgoing transitions: to room_dw_ranking_hub.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ranking_c`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_ranking_c_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_ranking_c`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_ranking_hub.
- Outgoing transitions: to room_dw_ranking_hub.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ranking_hub`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_ranking_hub_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_ranking_hub`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_green_room; door from
  room_dw_ranking_a; door from room_dw_ranking_b; door from room_dw_ranking_c;
  door from room_dw_ranking_t; door from room_dw_ranking_z_hallway.
- Outgoing transitions: to room_dw_green_room; to room_dw_ranking_a; to
  room_dw_ranking_b; to room_dw_ranking_c; to room_dw_ranking_t; to
  room_dw_ranking_z_hallway.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ranking_t`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ranking_t_floor`, `obj_dw_ranking_t_overlay`,
  `obj_dw_ranking_t_screens`, `obj_dw_ranking_t_shadowmaker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_room_ranking_t`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_ranking_hub.
- Outgoing transitions: to room_dw_ranking_hub.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ranking_z`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_z_rank_overlay`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`,
  `obj_room_ranking_z`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_ranking_z_hallway.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_ranking_z_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_z_rank_overlay`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`,
  `obj_room_ranking_z_hallway`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_inbetweenhall; door from
  room_dw_ranking_hub; door from room_dw_ranking_z.
- Outgoing transitions: to room_dw_ranking_hub.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_rhythm`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_GSB02`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_rhythmgame`, `obj_solidblock_32`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_rhythm_countdown`

- Area: Rhythm subsystem.
- Runtime role/status: border/tension handling includes this countdown room; no
  ingress transition verified; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_room_rhythm_countdown`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_rhythm_empty`

- Area: Rhythm subsystem.
- Runtime role/status: empty rhythm staging/template asset; no runtime dispatch
  verified; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_room_rhythm_empty`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_snow_zone`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch3_BTB04`, `obj_ch3_GSB05`, `obj_ch3_PTB01`,
  `obj_ch3_PTB02`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_snow_zone_parallax`, `obj_mainchara`, `obj_markerAny`,
  `obj_savepoint`, `obj_solidblock_diagonal_32`, `obj_solidblocksized`,
  `obj_sul`.
- Incoming transitions: door from room_dw_puzzlecloset_2; door from
  room_dw_puzzlecloset_3; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_puzzlecloset_2.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_snow_zone_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_BTB06`, `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_snow_zone_east_door`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_snow_zone_east_door`, `obj_solidblocksized`,
  `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: placed obj_doorAny and obj_room_snow_zone_east_door
  drive the snow-zone connector.
- Outgoing transitions: to room_town_krisyard_dark.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_susiezilla`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_GSC05`, `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_susiezilla_empty`

- Area: TV World.
- Runtime role/status: Susiezilla empty-stage presentation driven by
  obj_room_susiezilla_empty; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_room_susiezilla_empty`, `obj_solidblock_32`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_audiencepits`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_teevie_audiencepits`, `obj_dw_teevie_audiencepits_stealthtrig`,
  `obj_dw_teevie_bg`, `obj_dw_teevie_cameras_cheer`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: TV stealth controller explicitly checks
  room_dw_teevie_audiencepits and its placed trigger drives the segment.
- Outgoing transitions: to room_dw_teevie_rhythm.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_bonus_zone`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_teevie`, `obj_room_teevie_bonus_zone`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_maze_quiz; door from
  room_dw_tv_closet.
- Outgoing transitions: to room_dw_teevie_maze_quiz; to room_dw_tv_closet.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_chef`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_teevie`, `obj_room_teevie_chef`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_cutscene_final; door from
  room_dw_teevie_dust; door from room_dw_teevie_maze; door from
  room_dw_teevie_maze; door from room_dw_teevie_maze; door from
  room_dw_teevie_stealth_d.
- Outgoing transitions: to room_dw_teevie_dust; to room_dw_teevie_maze; to
  room_dw_teevie_stealth_d.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_cowboy_zone_01_after`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_funny_stanchion_controller`,
  `obj_dw_ch3_teevie_floor_light_controller`, `obj_dw_ch3_teevie_screen_gold`,
  `obj_dw_teevie_statue`, `obj_mainchara`, `obj_markerAny`,
  `obj_room_teevie_cowboy_after_01`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_cowboy_zone_01_intro; door from
  room_dw_teevie_large_01; runtime dispatch.
- Outgoing transitions: to room_dw_teevie_cowboy_zone_01_intro; to
  room_dw_teevie_large_01.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_cowboy_zone_01_intro`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_teevie_floor_light_controller`, `obj_mainchara`, `obj_markerAny`,
  `obj_posterchecker`, `obj_room_teevie_cowboy_intro_01`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_cowboy_zone_01_after; door from
  room_dw_teevie_intro.
- Outgoing transitions: to room_dw_teevie_cowboy_zone_01_after; to
  room_dw_teevie_intro.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_cowboy_zone_02_after`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_teevie_cowboy_after_02`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_shadow_guys; runtime dispatch.
- Outgoing transitions: to room_dw_teevie_cowboy_zone_02_intro; to
  room_dw_teevie_shadow_guys.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_cowboy_zone_02_intro`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_posterchecker`, `obj_room_teevie_cowboy_intro_02`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_jail2; door from
  room_dw_teevie_cowboy_zone_02_after.
- Outgoing transitions: to room_dw_b3bs_jail2.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_cutscene_final`

- Area: TV World.
- Runtime role/status: TV staging asset with placed generic doors; no exact
  transition branch verified; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_teevie_chef; to room_dw_teevie_preview.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_dust`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_BTB02`, `obj_ch3_BTB03`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dustpile`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_chef; door from
  room_dw_teevie_dust_south; door from room_dw_teevie_preview.
- Outgoing transitions: to room_dw_teevie_chef; to room_dw_teevie_dust_south; to
  room_dw_teevie_preview.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_dust_south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_dw_wobbler`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`, `obj_npc_room`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_zapper_c; door from
  room_dw_teevie_dust.
- Outgoing transitions: to room_dw_b3bs_zapper_c; to room_dw_teevie_dust.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_failure_cage`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_stealth.
- Outgoing transitions: to room_dw_teevie_stealth.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_intro`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_funny_stanchion_controller`, `obj_dw_ch3_teevie_floor_light`,
  `obj_dw_ch3_teevie_floor_light_controller`, `obj_dw_ch3_teevie_screen_gold`,
  `obj_dw_teevie_bg`, `obj_dw_teevie_cameras`, `obj_dw_teevie_statue`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_teevie`, `obj_posterchecker`,
  `obj_room_teevie_intro`, `obj_savepoint`, `obj_shortcut_door`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_backstage; door from
  room_dw_teevie_cowboy_zone_01_intro.
- Outgoing transitions: to room_dw_backstage; to
  room_dw_teevie_cowboy_zone_01_intro.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_large_01`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_funny_stanchion_controller`, `obj_dw_ch3_teevie_floor_light`,
  `obj_dw_ch3_teevie_floor_light_controller`, `obj_dw_ch3_teevie_screen_gold`,
  `obj_dw_teevie_bg`, `obj_dw_teevie_cameras`, `obj_dw_teevie_statue`,
  `obj_mainchara`, `obj_markerAny`, `obj_posterchecker`,
  `obj_room_teevie_large_01`, `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_b3bs_lancerget; door from
  room_dw_teevie_cowboy_zone_01_after; door from room_dw_teevie_large_02.
- Outgoing transitions: to room_dw_b3bs_lancerget; to
  room_dw_teevie_cowboy_zone_01_after; to room_dw_teevie_large_02.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_large_02`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_funny_stanchion_controller`, `obj_dw_ch3_teevie_floor_light`,
  `obj_dw_ch3_teevie_floor_light_controller`, `obj_dw_ch3_teevie_screen_gold`,
  `obj_dw_teevie_statue`, `obj_mainchara`, `obj_markerAny`,
  `obj_room_teevie_large_02`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_mysterypuzzle; door from
  room_dw_teevie_large_01; door from room_dw_teevie_susiezilla.
- Outgoing transitions: to room_dw_b3bs_mysterypuzzle; to
  room_dw_teevie_large_01; to room_dw_teevie_susiezilla.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_lightmaze`

- Area: Area not established.
- Runtime role/status: TV light-maze/stealth challenge driven by
  obj_dw_teevie_lightmaze; verified production reachable.
- Important controllers: `obj_board_trigger`, `obj_darkcontroller`,
  `obj_dw_ch3_funny_stanchion_controller`, `obj_dw_teevie_bg`,
  `obj_dw_teevie_cameras_cheer`, `obj_dw_teevie_cameras_crowd`,
  `obj_dw_teevie_lightmaze`, `obj_dw_teevie_stealth_chaselamp`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_solidblocksized`,
  `obj_treasure_room`, `obj_triggervolume`.
- Incoming transitions: obj_dw_teevie_lightmaze and stealth chase-lamp code
  explicitly drive this TV maze segment.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_maze`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_camera_controller`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_teevie_bg`, `obj_dw_teevie_maze`,
  `obj_dw_teevie_maze_zapperpair`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_chef; door from
  room_dw_teevie_maze_chef; door from room_dw_teevie_maze_final; door from
  room_dw_teevie_maze_points.
- Outgoing transitions: to room_dw_teevie_chef; to room_dw_teevie_chef; to
  room_dw_teevie_chef; to room_dw_teevie_rhythm; to room_dw_teevie_sams.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_maze_chef`

- Area: TV World.
- Runtime role/status: Chef maze/minigame staging tied to obj_chefs_game;
  verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: TV chef minigame controller context runtime controller
  and placed obj_doorAny staging.
- Outgoing transitions: to room_dw_teevie_maze.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_maze_final`

- Area: TV World.
- Runtime role/status: TV staging asset with placed generic doors; no exact
  transition branch verified; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_teevie_maze.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_maze_points`

- Area: TV World.
- Runtime role/status: TV staging asset with placed generic doors; no exact
  transition branch verified; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_teevie_maze.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_maze_quiz`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_teevie_bg`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_teevie`,
  `obj_room_teevie_maze_quiz`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_bonus_zone; door from
  room_dw_teevie_sams; door from room_dw_teevie_shuttahmaze; door from
  room_dw_teevie_stealth_d.
- Outgoing transitions: to room_dw_teevie_bonus_zone; to room_dw_teevie_sams; to
  room_dw_teevie_shuttahmaze; to room_dw_teevie_stealth_d.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_preview`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_funny_stanchion_controller`, `obj_dw_ch3_teevie_screen_gold`,
  `obj_dw_teevie_bg`, `obj_dw_teevie_statue`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_posterchecker`, `obj_room_tvland_preview`,
  `obj_shortcut_door`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_green_room; door from
  room_dw_teevie_cutscene_final; door from room_dw_teevie_dust; door from
  room_dw_teevie_preview_south.
- Outgoing transitions: to room_dw_green_room; to room_dw_teevie_dust.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_preview_south`

- Area: TV World.
- Runtime role/status: TV staging asset with placed generic doors; no exact
  transition branch verified; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_teevie_preview.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_rhythm`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_room_teevie_rhythm`, `obj_savepoint`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_audiencepits; door from
  room_dw_teevie_maze; door from room_dw_teevie_shuttahmaze; door from
  room_dw_teevie_stealth; door from room_dw_teevie_stealth_c.
- Outgoing transitions: to room_dw_teevie_shuttahmaze; to
  room_dw_teevie_stealth_c.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_ribbick`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_stealth.
- Outgoing transitions: to room_dw_teevie_stealth.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_ribbicks_a`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_b3bs_trashcan`, `obj_dw_teevie_ribbicks_a`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_solidblocksized`, `obj_solidenemy`.
- Incoming transitions: door from room_dw_b3bs_zapper_a; door from
  room_dw_b3bs_zapper_b.
- Outgoing transitions: to room_dw_b3bs_zapper_a; to room_dw_b3bs_zapper_b.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_ribbicks_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_b3bs_trashcan`, `obj_dw_teevie_ribbicks_b`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_solidblocksized`,
  `obj_triggervolume`.
- Incoming transitions: door from room_dw_b3bs_jail2; door from
  room_dw_b3bs_zapper_b.
- Outgoing transitions: to room_dw_b3bs_jail2; to room_dw_b3bs_zapper_b.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_sams`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_teevie_sams`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_maze; door from
  room_dw_teevie_maze_quiz.
- Outgoing transitions: to room_dw_teevie_maze_quiz.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_shadow_guys`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_camera`,
  `obj_board_controller`, `obj_board_solid`, `obj_board_trigger`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_ch3_b3bs_office_paperstack`,
  `obj_dw_ch3_b3bs_officesign`, `obj_dw_teevie_shadow_guys`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_solidblock_diagonal_32`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_cooltrashy; door from
  room_dw_b3bs_cooltrashy; door from room_dw_teevie_cowboy_zone_02_after; door
  from room_dw_teevie_stealth_c.
- Outgoing transitions: to room_dw_b3bs_cooltrashy; to room_dw_b3bs_cooltrashy;
  to room_dw_teevie_cowboy_zone_02_after; to room_dw_teevie_stealth_c.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_shuttahmaze`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_camera_controller`,
  `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_teevie_floor_light_controller`, `obj_dw_teevie_bg`,
  `obj_dw_teevie_cameras_cheer`, `obj_dw_teevie_shuttahmaze`,
  `obj_dw_teevie_tv_screens`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_trigger`, `obj_triggervolume`.
- Incoming transitions: door from room_dw_teevie_maze_quiz; door from
  room_dw_teevie_rhythm.
- Outgoing transitions: to room_dw_teevie_maze_quiz; to room_dw_teevie_rhythm.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_stealth`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_teevie_bg`, `obj_dw_teevie_cameras`, `obj_dw_teevie_stealth`,
  `obj_dw_teevie_stealth_chaselamp`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_failure_cage; door from
  room_dw_teevie_ribbick.
- Outgoing transitions: to room_dw_teevie_failure_cage; to
  room_dw_teevie_rhythm; to room_dw_teevie_ribbick.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_stealth_c`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_teevie_stealth_c`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_rhythm; door from
  room_dw_teevie_shadow_guys.
- Outgoing transitions: to room_dw_teevie_rhythm; to room_dw_teevie_shadow_guys.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_stealth_d`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_b3bs_stealth`, `obj_b3bs_stealtharea`,
  `obj_b3bs_stealthSolid`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_teevie_stealth_d`, `obj_mainchara`, `obj_markerAny`,
  `obj_room_teevie_stealth_d`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_teevie_chef; door from
  room_dw_teevie_maze_quiz.
- Outgoing transitions: to room_dw_teevie_chef; to room_dw_teevie_maze_quiz.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_susiebridge`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_b3bs_console`, `obj_board_bridgespawner`,
  `obj_board_camera`, `obj_board_controller`, `obj_board_event_bridgepuzzle`,
  `obj_board_flowers`, `obj_board_grabbablegrass`, `obj_board_resettile`,
  `obj_board_solid`, `obj_board_treespawner`, `obj_board_watertile`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_teevie_susiebridge`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_b3bs_cooltrashy.
- Outgoing transitions: to room_dw_b3bs_cooltrashy.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_susiezilla`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_confettikiller`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_ch3_funny_stanchion_controller`, `obj_dw_teevie_bg`,
  `obj_dw_teevie_susiezilla`, `obj_dw_teevie_susiezilla_ropeenemy`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`,
  `obj_solidblock_diagonal_32`, `obj_solidblocksized`,
  `obj_susiezilla_house_single`.
- Incoming transitions: door from room_dw_b3bs_jail1; door from
  room_dw_teevie_large_02.
- Outgoing transitions: to room_dw_b3bs_jail1; to room_dw_teevie_large_02.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_teevie_watercooler`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ch3_teevie_floor_light`, `obj_dw_ch3_teevie_floor_light_controller`,
  `obj_dw_teevie_bg`, `obj_dw_teevie_watercooler`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_b3bs_zapper_b.
- Outgoing transitions: to room_dw_b3bs_zapper_b.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_tv_closet`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_closet`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_sdr`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_teevie_bonus_zone.
- Outgoing transitions: to room_dw_teevie_bonus_zone.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_tv_curtain`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_teevie_bg`, `obj_dw_teevie_cameras`, `obj_dw_tv_curtain_tennanpc`,
  `obj_mainchara`, `obj_room_curtain`, `obj_sdl_dark`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_ch3_gameshowroom.
- Conditions: No additional condition verified.

### Chapter 3: `room_dw_tv_cutscene1g`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_GSA01G`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_ch3_gameshowroom.
- Conditions: No additional condition verified.

### Chapter 3: `room_ed`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_credits_ch3`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_empty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 3: `room_flowershop_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorX`, `obj_flowershop_event`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorB from room_flowershop_2f
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_flowershop_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_flowershop_event`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_sign`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_flowershop_1f
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_gameover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_gameover_init`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_genanimtest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_knight_swordtunnelanim`,
  `obj_mainchara`, `obj_solidblock_32`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_gif_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_sprite_catalog`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_gms_debug_failsafe`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_gamecontroller`, `obj_gms_debug_failsafe`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_GMS2_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_soliddark`, `obj_swordarea`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_graveyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_markerX`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_sur`, `obj_town_event`, `obj_town_graveyard`.
- Incoming transitions: enabled placed obj_doorA from room_town_church resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_hospital_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_hospital_lobby
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_hospital_rudy resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_hospital_lobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorW`, `obj_mainchara`,
  `obj_markerB`, `obj_markerw`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorB from room_hospital_hallway
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_hospital_room2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_hospital_rudy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_npc_rudy`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_hospital`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_hospital_hallway
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `ROOM_INITIALIZE`

- Area: Bootstrap.
- Runtime role/status: runtime initialization room; bootstrap.
- Important controllers: `obj_gamecontroller`, `obj_initializer2`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 3: `room_insidecloset`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_intro`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_intro_ch3`.
- Incoming transitions: runtime variable dispatch to room_intro; runtime
  variable dispatch to room_intro.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_krishallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_doorC`, `obj_hallway_mirror`,
  `obj_mainchara`, `obj_markerA`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_solidlong`.
- Incoming transitions: enabled placed obj_doorA from room_krisroom resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_krisroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_krisroom`, `obj_mainchara`,
  `obj_markerB`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorB from room_krishallway resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_legend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_legend`.
- Incoming transitions: runtime variable dispatch to room_legend; runtime
  variable dispatch to room_legend.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_legend_neo`

- Area: Development.
- Runtime role/status: Sunkus-key debug Legend destination from obj_mainchara
  input; uncertain-no-ingress.
- Important controllers: `obj_legend_neo`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_lerptest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_lerptest`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_library`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorW`, `obj_doorX`,
  `obj_mainchara`, `obj_markert`, `obj_markerw`, `obj_markerX`,
  `obj_npc_facing`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_town_library`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_lw_computer_lab`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_lw_conbini`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorw_musfade`,
  `obj_mainchara`, `obj_markerv`, `obj_musicer_conbini`, `obj_npc_conbini`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_lw_icee_pizza`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorW`, `obj_mainchara`,
  `obj_markert`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_soliddark`, `obj_town_pizza`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_lw_library_upstairs`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorW`, `obj_mainchara`, `obj_markert`,
  `obj_npc_library_upstairs`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdl_dark`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_lw_police`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_mainchara`, `obj_markerv`,
  `obj_npc_police`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_town_south.
- Conditions: No additional condition verified.

### Chapter 3: `room_overworldBulletEnemyTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_overworld_bulletarea`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_perspective_testing`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_board_solidenemy`, `obj_darkcontroller`,
  `obj_dw_green_room_bg_fx`, `obj_dw_green_room_tile_fx`, `obj_mainchara`,
  `obj_musicer_green_room`, `obj_perspective_test`, `obj_solidblocksized`,
  `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_rhythmgame_editor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_rhythmgame_editor`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_rhythmgame_tenna_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_rhythmgame_tenna_tester`, `obj_solidblock_32`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_school_unusedroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_unusedclassevent`.
- Incoming transitions: non-production unused classroom; excluded from ordered
  adjacency and only referenced by unused/fountain cleanup/readable-room
  compatibility code.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_schooldoor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkdoor`, `obj_doorC`, `obj_doorD`,
  `obj_mainchara`, `obj_markerC`, `obj_markerD`, `obj_markerX`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_schoollobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_doorA`, `obj_doorAny`, `obj_doorB`, `obj_doorC`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_markerX`,
  `obj_overworldc`, `obj_readable_room1`, `obj_room_schoollobby`,
  `obj_solidblock`, `obj_sul`.
- Incoming transitions: door from room_town_school; enabled placed obj_doorA
  from room_torielclass resolves room_goto_next via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_town_school.
- Conditions: doorFadeMusic = global.plot < 200;.

### Chapter 3: `room_shadowmantle`

- Area: Area not established.
- Runtime role/status: Board-game traversal/minigame space driven by
  obj_board_controller; verified production reachable.
- Important controllers: `obj_board_camera`, `obj_board_controller`,
  `obj_board_solid`, `obj_darkcontroller`, `obj_gameshow_swordroute`,
  `obj_mainchara`, `obj_mainchara_board`, `obj_shadow_mantle_bg`,
  `obj_shadow_mantle_enemy`, `obj_shadow_mantle_path`,
  `obj_shadowmantle_crtcontroller`, `obj_soliddark`.
- Incoming transitions: sword-route controller and obj_mainchara_board
  explicitly initialize the Shadow Mantle battle room.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_shadowmantle_movementExample`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_shadowmantleExample`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_shootout`

- Area: TV World.
- Runtime role/status: Shootout minigame staging driven by
  obj_shootout_controller and obj_ch3_GSD03; verified production reachable.
- Important controllers: `obj_ch3_GSD03`, `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: shootout minigame context runtime controller and placed
  obj_ch3_GSD03.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_shop_music`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop_music`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_shop1`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop1`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_sound_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_soundtester`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_sprite_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_spritecomparer`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_susiezilla`

- Area: TV World.
- Runtime role/status: Susiezilla destruction minigame driven by
  obj_susiezilla_controller; verified production reachable.
- Important controllers: `obj_building_breakable`, `obj_car_breakable`,
  `obj_darkcontroller`, `obj_house_breakable`, `obj_mainchara`,
  `obj_solidblock`, `obj_susiezilla`, `obj_susiezilla_controller`,
  `obj_tree_breakable`.
- Incoming transitions: placed obj_susiezilla_controller drives the destruction
  minigame.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_susiezilla_singleScreenMockup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_susiezilla_test_menu`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_tennaAnimTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_solidblock_32`, `obj_tennaPresetTester`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_tennaCutsceneTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_title_placeholder`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_title_placeholder`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 3: `room_torbathroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_sur`, `obj_town_event`.
- Incoming transitions: enabled placed obj_doorA from room_torhouse resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_torhouse`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorD`, `obj_doorX_musfade`,
  `obj_event_room`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerX`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdl`, `obj_sdr`, `obj_solidblock`, `obj_solidlong`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorB from room_torbathroom resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_torhouse_sepia`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch3_BTB05`, `obj_ch3_BTB05_screenbloom`,
  `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_torielclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_mainchara`,
  `obj_markerB`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_torielclass_event`.
- Incoming transitions: enabled placed obj_doorB from room_schoollobby resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_torroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_apartments`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_church`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_ch3_PTB04_church`,
  `obj_church_event`, `obj_doorA`, `obj_doorC_musfade`, `obj_doorD`,
  `obj_doorX`, `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_markerD`,
  `obj_markerX`, `obj_musicer_town`, `obj_overworldc`, `obj_sdl`, `obj_sdr`,
  `obj_solidblock`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_graveyard resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_krisyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorC`, `obj_doorX_musfade`, `obj_mainchara`,
  `obj_markerD`, `obj_markerX`, `obj_musicer_town`, `obj_npc_sign`,
  `obj_overworldc`, `obj_sdl`, `obj_sdr`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_krisyard_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_ch3_PTB04_krisyard`,
  `obj_doorC`, `obj_mainchara`, `obj_markerD`, `obj_npc_sign`, `obj_overworldc`,
  `obj_sdl`, `obj_sdr`, `obj_solidblock`.
- Incoming transitions: door from room_dw_snow_zone_east_door; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_mid`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorC`, `obj_doorD`,
  `obj_doorW`, `obj_doorw_musfade`, `obj_doorX`, `obj_mainchara`, `obj_markerC`,
  `obj_markerD`, `obj_markert`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_town`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_mid_diner`, `obj_solidblock`, `obj_town_event`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_north`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorC`, `obj_doorD`, `obj_doorX`,
  `obj_flowerking`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerD`, `obj_markerX`, `obj_musicer_town`, `obj_npc_facing`,
  `obj_npc_room`, `obj_npc_sign`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`, `obj_town_north`.
- Incoming transitions: enabled placed obj_doorB from room_beach resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_northwest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_school`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_doorAny`, `obj_doorB`, `obj_mainchara`,
  `obj_markerA`, `obj_markerX`, `obj_musicer_town`, `obj_overworldc`, `obj_sdr`,
  `obj_solidblock`.
- Incoming transitions: door from room_schoollobby; enabled placed obj_doorA
  from room_town_south resolves room_goto_next via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_schoollobby.
- Conditions: doorFadeMusic = global.plot < 200;.

### Chapter 3: `room_town_shelter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_ch3_PTB04_shelter`,
  `obj_doorD_musfade`, `obj_mainchara`, `obj_markerC`, `obj_overworldc`,
  `obj_sdl`, `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`,
  `obj_town_shelter_event`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_town_south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_doorC`,
  `obj_doorD`, `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markerB`,
  `obj_markerC`, `obj_markerD`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_town`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_south`, `obj_room_town_south_alphys`, `obj_solidblock`,
  `obj_sul`, `obj_town_event`.
- Incoming transitions: door from room_lw_police; enabled placed obj_doorB from
  room_town_school resolves room_goto_previous via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 3: `room_townhall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_room`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdl`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

## Chapter 4 (328 assets)

### Chapter 4: `PLACE_CONTACT`

- Area: Player flow.
- Runtime role/status: contact or chapter-entry runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_CONTACT_old`.
- Incoming transitions: runtime dispatch; runtime variable dispatch to
  PLACE_CONTACT.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `PLACE_DOG`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `PROCESS_DOG`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `PLACE_DOGCHECK2`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_dogcheck2`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `PLACE_FAILURE`

- Area: Player flow.
- Runtime role/status: failure/game-over runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_FAILURE`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `PLACE_LOGO`

- Area: Player flow.
- Runtime role/status: logo transition destination; verified production
  reachable.
- Important controllers: `PROCESS_LOGO`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `PLACE_MENU`

- Area: Player flow.
- Runtime role/status: title/menu runtime destination; verified production
  reachable.
- Important controllers: `DEVICE_MENU`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `PLACE_NAMING_JIKKEN`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `DEVICE_NAMER`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `room_alphysalley`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_doorW`,
  `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerw`, `obj_npc_room`,
  `obj_overworldc`, `obj_room_town_alphysalley`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_alphysclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_alphysdesk`, `obj_classscene`, `obj_mainchara`,
  `obj_markerA`, `obj_overworldc`, `obj_readable_room1`, `obj_schooldesk`,
  `obj_solidblock`, `obj_tem_school`, `obj_town_school_alphysclass`.
- Incoming transitions: enabled placed obj_doorA from room_schoollobby resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_battletest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_battletester`, `obj_chaseenemy`,
  `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `room_beach`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_ch4_LWF02A`, `obj_doorB`,
  `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerA`, `obj_npc_room`,
  `obj_npc_sign`, `obj_onion_event`, `obj_overworldc`, `obj_room_beach`,
  `obj_solidblock`, `obj_wave_fx`.
- Incoming transitions: enabled placed obj_doorA from room_town_north resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_bullettest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_bullettester`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch; debug/test runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `room_bullettest_new`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_bullettester_new`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `room_castle_tutorial`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_tutorial`, `obj_darkcontroller`,
  `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_darkcastle`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_cc_clover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorD_musfade`,
  `obj_mainchara`, `obj_markerC`, `obj_npc_room`, `obj_npc_room_animated`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_cc_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_ch4_DCC04`, `obj_ch4_PDC01A`, `obj_darkfountain`.
- Incoming transitions: door from room_dw_churchc_final_prophecy; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_cc_lancer`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_bluhpainting`,
  `obj_darkcontroller`, `obj_doorW`, `obj_hootpainting`, `obj_mainchara`,
  `obj_markerX`, `obj_purplegrass`, `obj_readable_room1`,
  `obj_room_castle_lancer`, `obj_solidblockDark`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_chapter_continue`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chapter_continue`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_cutscene_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_conveyorbelt`, `obj_cutscene_test`,
  `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorAny`, `obj_forcefield`,
  `obj_mainchara`, `obj_npc_sign`, `obj_soliddark`, `obj_sticky_example`,
  `obj_swordobj_example`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_krishallway.
- Conditions: No additional condition verified.

### Chapter 4: `room_cutscene_tester_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_example_cutscene_b`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dark_twostoryTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay_twofloor`,
  `obj_dw_church_pushableshelf_darklight`, `obj_dw_church_shelflightarea`,
  `obj_fully_lit_churchWindow_tall`, `obj_heightfloor`, `obj_lightsource_floor`,
  `obj_mainchara`, `obj_shelves_resetbell`, `obj_solidblockDark`,
  `obj_solidenemy`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_DARKbase_GMS2`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 4: `room_DARKempty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 4: `room_darkness_example`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_dw_church_prophecy`, `obj_lightsource`, `obj_mainchara`,
  `obj_npc_room_animated`, `obj_roomglow`, `obj_solidblocksized`,
  `obj_titan_star_dissolve`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_darkness_example_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_illusion`,
  `obj_darkness_interactable_example`, `obj_darkness_overlay`,
  `obj_lightsource`, `obj_lightsource_window`, `obj_mainchara`,
  `obj_music_wobbler`, `obj_npc_room_animated`, `obj_solidblocksized`,
  `obj_window_shadow_maker`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_battle`, `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_battleBalloon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_ballooner`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_choicer_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_choicer`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_choicer_light`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_choicer`, `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_color`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_swatchling`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_layeredLevelTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climbingarea`, `obj_darkcontroller`,
  `obj_heightfloor`, `obj_heightfloor_changer`, `obj_mainchara`,
  `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_loc`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_loc`, `obj_hallway_mirror`, `obj_mainchara`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_solidlong`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_pianotest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_dw_church_organ`,
  `obj_kris_pianopuppet`, `obj_mainchara`, `obj_solidblock`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_smallface`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_smallfacetester`, `obj_mainchara`,
  `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_smallface_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_smallfacetester`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_debug_windowEffect`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_dw_church_window_parallax`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_diner`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_PDC05A`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_sur`, `obj_town_diner`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_3d_tower_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climbingarea`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_markerAny`, `obj_rotating_bg_controller`,
  `obj_rotating_tower_controller`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_area_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_dw_leave`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_room_castle_area_1`,
  `obj_sdl_dark`, `obj_sdr_dark`, `obj_soliddark`, `obj_sul_dark`,
  `obj_sur_dark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_cafe`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_darkcastle`, `obj_npc_cafe`,
  `obj_npc_castle_cafe`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: to room_dw_castle_town.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_dojo`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch2_dojo_allstarsPlaylist`, `obj_darkcontroller`,
  `obj_dojofx`, `obj_doorX`, `obj_mainchara`, `obj_markerX`, `obj_musicer_gen`,
  `obj_readable_room1`, `obj_room_castle_dojo`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_dungeon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_king`, `obj_room_dungeon_2f`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_east_door`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_castle_door`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_restaurant`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_npc_castle_bakery`, `obj_sdl`, `obj_sdr`, `obj_soliddark`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_rooms_kris`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_readable_room1`, `obj_room_castle_kris`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_ralsei_castle_2f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_rooms_kris_susie`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_castle_kris_susie`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_ralsei_castle_2f; door from
  room_dw_ralsei_castle_2f.
- Outgoing transitions: to room_dw_ralsei_castle_2f; to
  room_dw_ralsei_castle_2f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_rooms_queen`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_castletown_queen`, `obj_room_castle_queen`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_ralsei_castle_3f.
- Outgoing transitions: to room_dw_ralsei_castle_3f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_rooms_ralsei`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_PDC06B`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_readable_room1`,
  `obj_room_castle_ralsei`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_ralsei_castle_3f.
- Outgoing transitions: to room_dw_ralsei_castle_3f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_rooms_susie`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_readable_room1`, `obj_room_castle_susie`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_ralsei_castle_2f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_rooms_tenna`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tenna_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_castle_tenna`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_ralsei_castle_3f.
- Outgoing transitions: to room_dw_ralsei_castle_3f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_town`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_castle_cafe`,
  `obj_castle_dojo`, `obj_castle_music`, `obj_castle_restaurant`,
  `obj_castle_shop`, `obj_castle_torch`, `obj_castle_tv`, `obj_ch4_PDC06`,
  `obj_darkcontroller`, `obj_doorA`, `obj_doorAny`, `obj_doorX`,
  `obj_dw_ch3_funny_stanchion_controller`, `obj_mainchara`, `obj_markerAny`,
  `obj_markerB`, `obj_markerr`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_darkcastle`, `obj_room_castle_town`,
  `obj_room_castle_town_lancer`, `obj_savepoint`, `obj_sdl_dark`,
  `obj_sdr_dark`, `obj_solidblockDark`, `obj_solidblocksized`, `obj_sul`,
  `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: door from room_dw_castle_cafe; door from
  room_dw_castle_tv; enabled placed obj_doorB from room_dw_ralsei_castle_front
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_castle_cafe; to room_dw_castle_dojo; to
  room_dw_castle_restaurant; to room_dw_castle_tv; to room_shop_music; to
  room_shop1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_tv`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_ranking_hub_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_darkcastle`, `obj_room_castle_tv`,
  `obj_savepoint`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_town; door from
  room_dw_castle_tv_rhythm; door from room_dw_castle_tv_zone_1; door from
  room_dw_castle_tv_zone_battle; door from room_dw_castle_tv_zone_minigame.
- Outgoing transitions: to room_dw_castle_town; to room_dw_castle_tv_rhythm; to
  room_dw_castle_tv_zone_1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_tv_rhythm`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_blue_starry_wall`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_darkcastle`, `obj_room_castle_tv_rhythm`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_tv; runtime dispatch; runtime
  dispatch.
- Outgoing transitions: to room_dw_castle_tv.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_tv_zone_1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tv_zone_1_floor`,
  `obj_dw_tv_zone_overlay`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`,
  `obj_room_castle_tv_zone_1`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_tv; door from
  room_dw_castle_tv_zone_2.
- Outgoing transitions: to room_dw_castle_tv; to room_dw_castle_tv_zone_2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_tv_zone_2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tv_zone_2_floor`,
  `obj_dw_tv_zone_overlay`, `obj_mainchara`, `obj_markerAny`, `obj_miccheck`,
  `obj_mike_door`, `obj_musicer_gen`, `obj_room_castle_tv_zone_2`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_tv_zone_1; door from
  room_dw_castle_tv_zone_3.
- Outgoing transitions: to room_dw_castle_tv_zone_1; to
  room_dw_castle_tv_zone_3; to room_dw_castle_tv_zone_battle.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_tv_zone_3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tv_zone_3_floor`,
  `obj_dw_tv_zone_overlay`, `obj_mainchara`, `obj_markerAny`,
  `obj_mouse_drawer`, `obj_mouse_hat`, `obj_mouse_shelf`,
  `obj_room_castle_tv_zone_3`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_tv_zone_2.
- Outgoing transitions: to room_dw_castle_tv_zone_2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_tv_zone_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tv_zone_battle_floor`,
  `obj_dw_tv_zone_overlay`, `obj_mainchara`, `obj_markerAny`,
  `obj_room_castle_tv_zone_battle`, `obj_solidblockDark`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_castle_tv_zone_2.
- Outgoing transitions: to room_dw_castle_tv.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_tv_zone_minigame`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_andydebug`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tv_zone_minigame_floor`,
  `obj_dw_tv_zone_overlay`, `obj_mainchara`, `obj_markerAny`, `obj_miccheck`,
  `obj_mike_minigame_tv`, `obj_mike_slot`, `obj_musicer_darkcastle`,
  `obj_room_castle_tv_zone_minigame`, `obj_solidblockDark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_castle_tv.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_castle_west_cliff`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerD`, `obj_markerX`, `obj_npc_castle_cliff`, `obj_soliddark`,
  `obj_treasure_room`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_channelchange_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_screen_channel_change`,
  `obj_screen_channel_change_tester`, `obj_titan_distort`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_arena`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_arena`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_gerson_study`, `obj_solidblock_topleft_dark`,
  `obj_solidblock_topright_dark`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_gersonstudy.
- Outgoing transitions: to room_dw_church_gersonstudy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_b_intro`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCB01`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_solidblockDark`.
- Incoming transitions: placed obj_ch4_DCB01 drives the Church B introduction
  sequence.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bell_small_playable`, `obj_climb_climbable`,
  `obj_climbloc`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_bellclimb`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_church_crumbletower; door from
  room_dw_church_tower1.
- Outgoing transitions: to room_dw_church_crumbletower; to
  room_dw_church_tower1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellhall_bookroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCA09`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_doorAny`, `obj_dw_church_bellhall_bookroom`,
  `obj_dw_church_bellhall_bookroom_winglade`, `obj_genmarker`, `obj_krmarker`,
  `obj_light_window_textureless_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_sumarker`.
- Incoming transitions: door from room_dw_church_bellhall_curtain; door from
  room_dw_church_bellhall_west; door from room_dw_church_darkclimb; door from
  room_dw_church_mizzleencounter; runtime dispatch.
- Outgoing transitions: to room_dw_church_bellhall_curtain; to
  room_dw_church_mizzleencounter.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellhall_central`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_organ`, `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_bellhall_east; door from
  room_dw_church_bellhall_west.
- Outgoing transitions: to room_dw_church_bellhall_east; to
  room_dw_church_bellhall_west.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellhall_curtain`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_church_bellhall_curtain`,
  `obj_dw_church_bellhall_curtain_vfx`, `obj_genmarker`,
  `obj_light_window_textureless_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_bellhall_bookroom; runtime
  dispatch.
- Outgoing transitions: to room_dw_church_bellhall_bookroom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellhall_east`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_bellhall_central; door from
  room_dw_church_statueclimb.
- Outgoing transitions: to room_dw_church_bellhall_central; to
  room_dw_church_statueclimb.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellhall_west`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_bellhall_central; door from
  room_dw_church_bellsareawest.
- Outgoing transitions: to room_dw_church_bellhall_bookroom; to
  room_dw_church_bellhall_central; to room_dw_church_bellsareawest.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellplay`

- Area: Church A.
- Runtime role/status: Playable bell subsystem driven by obj_bell_small_playable
  and obj_bellListener; verified production reachable.
- Important controllers: `obj_bell_small_playable`, `obj_bellListener`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_solidblockDark`.
- Incoming transitions: placed obj_bell_small_playable and obj_bellListener
  drive the playable bell subsystem.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bellsareawest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_church_bellhall_west; door from
  room_dw_church_slidingbookshelf; door from room_dw_church_stairs_west_bell.
- Outgoing transitions: to room_dw_church_bellhall_west; to
  room_dw_church_slidingbookshelf; to room_dw_church_stairs_west_bell.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_biblioxencounter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_bluebook`, `obj_dw_church_biblioxencounter`,
  `obj_light_window_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_bookshelfpuzzle; door from
  room_dw_church_bookshelfpuzzle_rev; door from room_dw_church_moneyfountain;
  door from room_dw_church_nwconnect.
- Outgoing transitions: to room_dw_church_bookshelfpuzzle_rev; to
  room_dw_church_moneyfountain; to room_dw_church_nwconnect.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bookcase`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCA05`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_dark_fire_puzzle; door from
  room_dw_church_lantern_hallway; door from room_dw_church_shadowgerson; door
  from room_dw_church_turtles.
- Outgoing transitions: to room_dw_church_lantern_hallway; to
  room_dw_church_shadowgerson; to room_dw_church_turtles.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bookenemywest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_librarybookenemy.
- Outgoing transitions: to room_dw_church_librarybookenemy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bookshelfpuzzle`

- Area: Area not established.
- Runtime role/status: Bookshelf puzzle driven by obj_dw_church_bookshelfpuzzle;
  verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_doorAny`, `obj_dw_church_bookshelfpuzzle`,
  `obj_floorTrigger`, `obj_krmarker`, `obj_light_window_mask`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church`, `obj_ramarker`, `obj_solid_temp`,
  `obj_solid_temp_edge_maker`, `obj_sumarker`, `obj_treasure_room`.
- Incoming transitions: obj_dw_church_bookshelfpuzzle is placed; church
  route/border code explicitly includes this puzzle room.
- Outgoing transitions: to room_dw_church_biblioxencounter; to
  room_dw_church_tallbookcases; to room_dw_church_worshiproom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bookshelfpuzzle_rev`

- Area: Area not established.
- Runtime role/status: Bookshelf puzzle driven by obj_dw_church_bookshelfpuzzle;
  verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_church_bookshelfpuzzle`, `obj_floorTrigger`,
  `obj_genmarker`, `obj_light_window_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church`, `obj_ramarker`, `obj_solid_temp`,
  `obj_solid_temp_edge_maker`, `obj_sumarker`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_church_biblioxencounter; door from
  room_dw_church_tallbookcases; door from room_dw_church_worshiproom.
- Outgoing transitions: to room_dw_church_biblioxencounter; to
  room_dw_church_tallbookcases; to room_dw_church_worshiproom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bookshelfpuzzle1`

- Area: Area not established.
- Runtime role/status: Bookshelf puzzle driven by obj_dw_church_bookshelfpuzzle;
  verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_bookshelfpuzzle1_old`, `obj_dw_church_remote_piano`,
  `obj_floorTrigger`, `obj_mainchara`, `obj_markerAny`, `obj_negasolid`,
  `obj_solid_temp`, `obj_solidenemy`.
- Incoming transitions: door from room_dw_church_bookshelfpuzzle2; door from
  room_dw_church_bookshelfpuzzle2; door from room_dw_church_librarybookenemy;
  door from room_dw_church_swingingbell; door from
  room_dw_church_tallbookcases_backup.
- Outgoing transitions: to room_dw_church_nwconnect; to
  room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_bookshelfpuzzle2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: ordered church route ordered route and placed
  door/controller flow identify the second bookshelf-puzzle segment.
- Outgoing transitions: to room_dw_church_bookshelfpuzzle1; to
  room_dw_church_bookshelfpuzzle1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_candlelighting`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_candle_lightable`,
  `obj_church_candleLighter`, `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_mainchara`, `obj_overworld_bulletarea`, `obj_parallaxer`, `obj_sdl_dark`,
  `obj_sdr_dark`, `obj_solidblockDark`, `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: placed obj_church_candleLighter and
  obj_church_candle_lightable drive the candle-lighting route segment.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_candlesroom1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_candle_lightable`,
  `obj_church_candleLighter`, `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_overworld_bulletarea`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_poolsroom1; door from
  room_dw_church_solowaterfall; door from room_dw_church_statueroom; door from
  room_dw_church_statueroom_old.
- Outgoing transitions: to room_dw_church_poolsroom1; to
  room_dw_church_solowaterfall; to room_dw_church_statueroom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_chase_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_ch4_DCA01`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_overworld_bulletarea`,
  `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_intro1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_claw`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCA08C`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_light_onHead`, `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_smallbells.
- Outgoing transitions: to room_dw_church_smallbells.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_climbtut`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bell_small_playable`, `obj_camera_clamper`,
  `obj_climb_climbable`, `obj_climb_notsafe`, `obj_climb_waterbucket`,
  `obj_climb_watergenerator`, `obj_climbloc`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_climbtut`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`, `obj_treasure_room`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_church_crumbletower; door from
  room_dw_church_fastwater; door from room_dw_church_tower1.
- Outgoing transitions: to room_dw_church_crumbletower; to
  room_dw_church_fastwater.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_crumbletower`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_destructableclimbarea`, `obj_climbloc`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_church_bellclimb; door from
  room_dw_church_climbtut; door from room_dw_church_shiftclimb.
- Outgoing transitions: to room_dw_church_bellclimb; to room_dw_church_climbtut.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_dark_fire_puzzle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_intro3.
- Outgoing transitions: to room_dw_church_bookcase; to room_dw_church_intro3; to
  room_dw_church_minorlegend.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_darkbell_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_lantern_hallway.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_darkclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climb_flamegenerator`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_darkclimb`, `obj_krmarker`,
  `obj_light_following`, `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`,
  `obj_solidblocksized`.
- Incoming transitions: placed obj_dw_church_darkclimb and obj_climbstarter
  drive the dark-climb route segment.
- Outgoing transitions: to room_dw_church_bellhall_bookroom; to
  room_dw_church_mizzleencounter.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_darkmaze`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_church_piano_hint`,
  `obj_church_piano_playable`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_darkmaze`, `obj_dw_church_glowtile`, `obj_genmarker`,
  `obj_krmarker`, `obj_magicalglass`, `obj_mainchara`, `obj_markerAny`,
  `obj_ramarker`, `obj_solidblockDark`, `obj_sumarker`, `obj_treasure_room`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_church_gersonstudy; door from
  room_dw_church_lantern_hallway.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_lantern_hallway.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_darkroom_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_darkroom1_bookshelfWall`, `obj_darkroom1_lanternDispenser1`,
  `obj_darkroom1_wallswitch`, `obj_doorAny`, `obj_lightTriggerArea`,
  `obj_mainchara`, `obj_markerAny`, `obj_overworld_bulletarea`,
  `obj_overworld_lanternflame_wall`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_minorlegend.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_darkroom1_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_darkroom1_bookshelfWall`, `obj_darkroom1_lanternDispenser1`,
  `obj_darkroom1_wallswitch`, `obj_doorAny`, `obj_lightTriggerArea`,
  `obj_mainchara`, `obj_markerAny`, `obj_overworld_bulletarea`,
  `obj_overworld_lanternflame_wall`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_intro3; to room_dw_church_minorlegend.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_dogclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_controller_new`, `obj_solidblockDark`,
  `obj_tower_dog_bone`, `obj_tower_dog_controller`,
  `obj_tower_dog_event_setter`, `obj_tower_dog_fx1`,
  `obj_tower_dog_ladder_fake`, `obj_treasure_room`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_gersonstudy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_fastwater`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climb_notsafe`, `obj_climb_waterbucket`, `obj_climb_watergenerator`,
  `obj_climbloc`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_church_climbtut; door from
  room_dw_church_shiftclimb; door from room_dw_church_tower1.
- Outgoing transitions: to room_dw_church_climbtut; to room_dw_church_tower1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_ch4_DCA12`, `obj_ch4_DCA12_darkfountain`.
- Incoming transitions: door from room_dw_church_staircase; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_fountainconnection`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cutscene_stairlooper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_botright_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblockDark`.
- Incoming transitions: placed obj_cutscene_stairlooper; context runtime
  controller drives the stair/fountain connection.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_staircase.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_gersonstudy`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch4_DCA07`, `obj_ch4_DCA10`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_gerson_study`, `obj_genmarker`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_gerson_study`, `obj_ramarker`, `obj_savepoint`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_botright_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblockDark`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_arena; door from
  room_dw_church_darkbell_old; door from room_dw_church_darkmaze; door from
  room_dw_church_dogclimb; door from room_dw_church_dogclimb; door from
  room_dw_church_fountainconnection; door from room_dw_church_guei; door from
  room_dw_church_northprophecies; door from room_dw_church_nwconnect; door from
  room_dw_church_rightconnect; door from room_dw_church_stairs_stainedglass;
  door from room_dw_church_stairs_topleft; door from
  room_dw_church_stairs_topright; door from room_dw_churchb_ripplepost; runtime
  dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_church_arena; to room_dw_church_darkmaze; to
  room_dw_church_northprophecies; to room_dw_church_nwconnect; to
  room_dw_church_rightconnect.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_glass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCA02`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_doorAny`, `obj_light_area_mask`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_savepoint; runtime dispatch.
- Outgoing transitions: to room_dw_church_savepoint.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_guei`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_lantern_hallway.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_gueitest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_church_lantern_arc`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_door_solid`, `obj_doorAny`,
  `obj_fully_lit_churchWindow_tall`, `obj_lightsource_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworld_bulletarea`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_lantern_hallway; to
  room_dw_church_lantern_hallway; to room_dw_church_lantern_hallway.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_holywatercooler`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climb_door`,
  `obj_climb_landingstrip`, `obj_climb_marker`, `obj_climb_waterbucket`,
  `obj_climb_watergenerator`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_dw_church_climbingcup`,
  `obj_dw_church_holywatercooler`, `obj_genmarker`, `obj_krmarker`,
  `obj_mainchara`, `obj_parallaxer`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_intro_gerson; door from
  room_dw_church_savepoint.
- Outgoing transitions: to room_dw_church_intro_gerson.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_intro_gerson`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bulletarea`, `obj_camera_clamper`,
  `obj_climb_climbable`, `obj_climb_door`, `obj_climb_marker`,
  `obj_climb_pathturner`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_darkroombg`,
  `obj_dw_church_glowtile`, `obj_dw_church_intro_gerson`,
  `obj_dw_church_staticlight_overworld`, `obj_krmarker`,
  `obj_lantern_shrinking`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church`, `obj_ow_pathingenemy`, `obj_ramarker`,
  `obj_solidblockDark`, `obj_solidenemy`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_holywatercooler; door from
  room_dw_church_intro_guei; door from room_dw_church_minorlegend; door from
  room_dw_church_shadowgerson.
- Outgoing transitions: to room_dw_church_holywatercooler; to
  room_dw_church_intro_guei; to room_dw_church_minorlegend; to
  room_dw_church_shadowgerson.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_intro_guei`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_nudger`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_doorAny`, `obj_dw_church_intro_guei`,
  `obj_dw_church_intro4_camera`, `obj_dw_church_singingcontroller`,
  `obj_dw_church_singingmizzle`, `obj_genmarker`, `obj_krmarker`,
  `obj_light_area_mask`, `obj_mainchara`, `obj_markerAny`, `obj_parallaxer`,
  `obj_solidblock_botright_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblockDark`, `obj_solidenemy`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_intro_gerson; door from
  room_dw_church_savepoint.
- Outgoing transitions: to room_dw_church_intro_gerson; to
  room_dw_church_savepoint.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_intro1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_church_a_intro1`, `obj_dw_church_intro1`,
  `obj_light_area_mask`, `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_chase_old; door from
  room_dw_church_intropiano; runtime dispatch.
- Outgoing transitions: to room_dw_church_intropiano.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_intro3`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cutscene_stairlooper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_legender`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_botright_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblockDark`, `obj_triggervolume`.
- Incoming transitions: door from room_dw_church_dark_fire_puzzle; door from
  room_dw_church_darkroom1_old.
- Outgoing transitions: to room_dw_church_dark_fire_puzzle.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_intropiano`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_piano_hint`, `obj_church_piano_playable`,
  `obj_church_triggerlight`, `obj_climb_climbable`, `obj_climb_door`,
  `obj_climb_marker`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_glowtile`,
  `obj_dw_church_intropiano`, `obj_krmarker`, `obj_light_following`,
  `obj_mainchara`, `obj_markerAny`, `obj_ramarker`, `obj_solidblockDark`,
  `obj_solidblocksized`, `obj_sumarker`.
- Incoming transitions: door from room_dw_church_intro1; door from
  room_dw_church_knightclimb; door from room_dw_church_staircase.
- Outgoing transitions: to room_dw_church_intro1; to room_dw_church_knightclimb;
  to room_dw_church_staircase.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_jackenstein`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bell_small_playable`, `obj_camera_clamper`,
  `obj_ch4_DCA08C`, `obj_ch4_DCA08D`, `obj_climb_climbable`,
  `obj_climb_waterbucket`, `obj_climb_watergenerator`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_darkslide_new`, `obj_doorAny`, `obj_dw_church_dark_maze_controller`,
  `obj_dw_church_jackenstein`, `obj_genmarker`, `obj_krmarker`,
  `obj_light_following`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`,
  `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`, `obj_treasure_room`,
  `obj_trigger`, `obj_triggervolume`.
- Incoming transitions: door from room_dw_church_nwconnect; door from
  room_dw_church_pianopuzzle.
- Outgoing transitions: to room_dw_church_nwconnect; to
  room_dw_church_pianopuzzle.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_knightclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_nudger`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_dw_church_knightclimb`,
  `obj_genmarker`, `obj_krmarker`, `obj_mainchara`, `obj_parallaxer`,
  `obj_proxycandle`, `obj_ramarker`, `obj_solidblockDark`, `obj_sumarker`,
  `obj_trigger`, `obj_window_knight_big_oscillate_r`,
  `obj_window_knight_oscillate`.
- Incoming transitions: door from room_dw_church_intropiano.
- Outgoing transitions: to room_dw_church_intropiano.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_knightclimb_post`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_knightclimbpost`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_gen`, `obj_ramarker`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblockDark`, `obj_solidblocksized`, `obj_sumarker`.
- Incoming transitions: door from room_dw_church_staircase; door from
  room_dw_churchc_superprophecies; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_church_staircase; to
  room_dw_churchc_superprophecies.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_lantern_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_lantern_hallway`, `obj_genmarker`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_ramarker`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_bookcase; door from
  room_dw_church_darkbell_old; door from room_dw_church_darkmaze; door from
  room_dw_church_guei; door from room_dw_church_lantern1_old; door from
  room_dw_church_lantern1_old; door from room_dw_church_lantern1_old; door from
  room_dw_church_lantern1_old_old; door from room_dw_church_lantern1_old_old;
  door from room_dw_church_lantern1_old_old; door from room_dw_church_turtles;
  door from room_dw_church_turtles.
- Outgoing transitions: to room_dw_church_bookcase; to room_dw_church_darkmaze.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_lantern_hallway_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_cutscene_stairlooper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_legender`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblockDark`, `obj_triggervolume`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_lantern1_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_church_lantern`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_door_solid`, `obj_doorAny`,
  `obj_fully_lit_churchWindow_tall`, `obj_lightsource_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworld_bulletarea`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_lantern_hallway; to
  room_dw_church_lantern_hallway; to room_dw_church_lantern_hallway.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_lantern1_old_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_church_lantern_arc`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_door_solid`, `obj_doorAny`,
  `obj_fully_lit_churchWindow_tall`, `obj_lightsource_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworld_bulletarea`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_lantern_hallway; to
  room_dw_church_lantern_hallway; to room_dw_church_lantern_hallway.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_lantern2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCA08A`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: placed obj_ch4_DCA08A drives the second lantern route
  sequence.
- Outgoing transitions: to room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_librarybookenemy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_bookenemywest; door from
  room_dw_church_stairs_topleft.
- Outgoing transitions: to room_dw_church_bookenemywest; to
  room_dw_church_bookshelfpuzzle1; to room_dw_church_stairs_topleft.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_minorlegend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_minorlegend`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblockDark`, `obj_treasure_room`, `obj_triggervolume`.
- Incoming transitions: door from room_dw_church_dark_fire_puzzle; door from
  room_dw_church_darkroom_old; door from room_dw_church_darkroom1_old; door from
  room_dw_church_intro_gerson.
- Outgoing transitions: to room_dw_church_intro_gerson.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_mizzleencounter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_church_mizzleencounter`, `obj_dw_church_watercooler`,
  `obj_genmarker`, `obj_light_window_textureless_mask`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church`, `obj_parallaxer`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblockDark`, `obj_solidenemy`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_bellhall_bookroom; door from
  room_dw_church_darkclimb; door from room_dw_church_organpuzzle.
- Outgoing transitions: to room_dw_church_bellhall_bookroom; to
  room_dw_church_organpuzzle.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_moneyfountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_moneyfountain`, `obj_dw_church_moneyfountainsprite`,
  `obj_dw_church_waterfall`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church`, `obj_parallaxer`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_church_biblioxencounter; door from
  room_dw_church_waterfallroom; door from room_dw_church_waterfalltearoom;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_church_biblioxencounter; to
  room_dw_church_waterfallroom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_northprophecies`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_nudger`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_northprophecies`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallaxer`, `obj_solidblockDark`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_gersonstudy; door from
  room_dw_church_staircase.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_staircase.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_npcroom_pools1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_npc_room`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_poolsroom1.
- Outgoing transitions: to room_dw_church_poolsroom1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_npcroom_shelfclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_shelfclimb2.
- Outgoing transitions: to room_dw_church_shelfclimb2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_nwconnect`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_nwconnect`, `obj_genmarker`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church`, `obj_parallaxer`, `obj_ramarker`,
  `obj_savepoint`, `obj_solidblocksized`, `obj_sumarker`.
- Incoming transitions: door from room_dw_church_biblioxencounter; door from
  room_dw_church_bookshelfpuzzle1; door from room_dw_church_gersonstudy; door
  from room_dw_church_jackenstein; door from room_dw_church_tallbookcases; door
  from room_dw_church_tallbookcases_backup.
- Outgoing transitions: to room_dw_church_biblioxencounter; to
  room_dw_church_gersonstudy; to room_dw_church_jackenstein; to
  room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_offering`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_shelfclimb2.
- Outgoing transitions: to room_dw_church_shelfclimb2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_organpuzzle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bells_parallaxer`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_doorAny`, `obj_dw_church_cupstack`,
  `obj_dw_church_organ`, `obj_dw_church_organpuzzle`, `obj_genmarker`,
  `obj_light_window_textureless_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_gen`, `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_church_mizzleencounter; door from
  room_dw_church_trueclimbadventure; door from
  room_dw_church_trueclimbadventure; runtime dispatch.
- Outgoing transitions: to room_dw_church_mizzleencounter; to
  room_dw_church_trueclimbadventure.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_pianopiece_left`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bulletarea`, `obj_church_piano_hint`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_glowtile`,
  `obj_dw_church_pianopiece_left`, `obj_floorswitch`, `obj_krmarker`,
  `obj_lantern_shrinking`, `obj_mainchara`, `obj_markerAny`,
  `obj_ow_pathingenemy_generator`, `obj_solidblocksized`, `obj_solidenemy_2`,
  `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_tallbookcases; door from
  room_dw_church_tallbookcases_backup.
- Outgoing transitions: to room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_pianopiece_left_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_glowtile`, `obj_dw_church_pianopiece_left_b`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblock_botleft_dark`,
  `obj_solidblock_botright_dark`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_pianopiece_right`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_doorAny`, `obj_dw_church_pianopiece_right`,
  `obj_floorTrigger`, `obj_genmarker`, `obj_krmarker`, `obj_light_window_mask`,
  `obj_mainchara`, `obj_markerAny`, `obj_ramarker`, `obj_solid_temp`,
  `obj_solid_temp_edge_maker`, `obj_sumarker`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_church_pianopiece_rightprophecy; door
  from room_dw_church_tallbookcases; door from
  room_dw_church_tallbookcases_backup.
- Outgoing transitions: to room_dw_church_pianopiece_rightprophecy; to
  room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_pianopiece_rightprophecy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_pianopiece_rightprophecy`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblock_botleft_dark`,
  `obj_solidblock_botright_dark`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_pianopiece_right.
- Outgoing transitions: to room_dw_church_pianopiece_right.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_pianopuzzle`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch4_DCA08B`, `obj_church_piano_playable`,
  `obj_darkcontroller`, `obj_darkness_overlay`, `obj_doorAny`,
  `obj_dw_church_pianopuzzle`, `obj_krmarker`, `obj_light_area_spot`,
  `obj_mainchara`, `obj_markerAny`, `obj_parallaxer`, `obj_ramarker`,
  `obj_savepoint`, `obj_solidblockDark`, `obj_sumarker`.
- Incoming transitions: door from room_dw_church_jackenstein; door from
  room_dw_church_tallbookcases; door from room_dw_church_tallbookcases_backup.
- Outgoing transitions: to room_dw_church_jackenstein; to
  room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_poolsroom1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_candlesroom1; door from
  room_dw_church_npcroom_pools1; door from room_dw_church_poolsroom1_east; door
  from room_dw_church_stairs_topright.
- Outgoing transitions: to room_dw_church_candlesroom1; to
  room_dw_church_npcroom_pools1; to room_dw_church_poolsroom1_east; to
  room_dw_church_stairs_topright.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_poolsroom1_east`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_poolsroom1.
- Outgoing transitions: to room_dw_church_poolsroom1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_poolsroom2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_poolsroom2south; door from
  room_dw_church_slidingbookshelf; door from room_dw_church_statueroom; door
  from room_dw_church_statueroom_old.
- Outgoing transitions: to room_dw_church_poolsroom2south; to
  room_dw_church_slidingbookshelf; to room_dw_church_statueroom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_poolsroom2south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_poolsroom2.
- Outgoing transitions: to room_dw_church_poolsroom2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_quicktest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_dw_church_quicktest`,
  `obj_genmarker`, `obj_mainchara`, `obj_solidblockDark`, `obj_trigger`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_rightconnect`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_church_climbingcup`, `obj_dw_church_cupstack`,
  `obj_dw_church_rightconnect`, `obj_dw_church_watercooler`, `obj_krmarker`,
  `obj_light_area_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church`, `obj_parallaxer`, `obj_ramarker`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_botright_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_church_gersonstudy; door from
  room_dw_church_stairspreview; door from room_dw_church_trueclimbadventure;
  door from room_dw_church_trueclimbadventure.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_stairspreview; to room_dw_church_trueclimbadventure.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_ripplepuzzle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_ch4_DCA04`,
  `obj_church_ripple_area_manager`, `obj_church_ripple_bell_area`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_glowtile`,
  `obj_genmarker`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_ramarker`, `obj_solidblockDark`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_turtles; runtime dispatch.
- Outgoing transitions: to room_dw_church_turtles.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_ripplepuzzle_postgers`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_ripplepuzzle_postgers`, `obj_krmarker`,
  `obj_magicalglass`, `obj_mainchara`, `obj_markerAny`, `obj_parallaxer`,
  `obj_ramarker`, `obj_solidblockDark`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_rippleworship; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_church_rippleworship; to
  room_dw_church_turtles.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_rippletest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_church_ripple_area`,
  `obj_church_ripple_area_manager`, `obj_church_ripple_bell_area`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_rippleworship`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_glowtile`, `obj_dw_church_rippleworship`, `obj_genmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_church_ripplepuzzle_postgers.
- Outgoing transitions: to room_dw_church_ripplepuzzle_postgers.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_ripseq1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dw_church_glowtile`,
  `obj_dw_church_ripseq1`, `obj_genmarker`, `obj_krmarker`, `obj_mainchara`,
  `obj_solidblockDark`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_ripseq2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dw_church_glowtile`,
  `obj_dw_church_ripseq2`, `obj_krmarker`, `obj_mainchara`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_savepoint`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_camera_nudger`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbloc`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_church_savepoint`, `obj_dw_church_singingcontroller`,
  `obj_dw_church_singingmizzle`, `obj_genmarker`, `obj_light_area_mask`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_dw_church`, `obj_parallaxer`,
  `obj_savepoint`, `obj_solidblock_botright_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblockDark`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_glass; door from
  room_dw_church_intro_guei.
- Outgoing transitions: to room_dw_church_glass; to
  room_dw_church_holywatercooler; to room_dw_church_intro_guei.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_secretpiano`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_secretpiano_playable`,
  `obj_climb_climbable`, `obj_climb_door`, `obj_climb_marker`, `obj_climbloc`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_dw_church_secretpiano`, `obj_krmarker`, `obj_mainchara`, `obj_ramarker`,
  `obj_solidblockDark`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_tallbookcases; runtime
  dispatch.
- Outgoing transitions: to room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_shadowgerson`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_camera_nudger`,
  `obj_darkcontroller`, `obj_darkness_overlay`, `obj_doorAny`,
  `obj_dw_church_shadowgerson`, `obj_genmarker`, `obj_krmarker`,
  `obj_light_area_mask`, `obj_mainchara`, `obj_markerAny`, `obj_parallaxer`,
  `obj_prophecytext`, `obj_ramarker`, `obj_solidblock_botright_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblockDark`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_church_bookcase; door from
  room_dw_church_intro_gerson.
- Outgoing transitions: to room_dw_church_bookcase; to
  room_dw_church_intro_gerson.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_shelfclimb1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_shelfclimb2.
- Outgoing transitions: to room_dw_church_shelfclimb2; to
  room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_shelfclimb2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_npcroom_shelfclimb; door from
  room_dw_church_offering; door from room_dw_church_shelfclimb1; door from
  room_dw_church_stairs_west_bell.
- Outgoing transitions: to room_dw_church_npcroom_shelfclimb; to
  room_dw_church_offering; to room_dw_church_shelfclimb1; to
  room_dw_church_stairs_west_bell.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_shiftclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bell_small_playable`, `obj_climb_climbable`,
  `obj_climb_mover`, `obj_climb_notsafe`, `obj_climb_waterbucket`,
  `obj_climb_watergenerator`, `obj_climbloc`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: placed obj_climbstarter and obj_climb_mover drive the
  shifting-climb route segment.
- Outgoing transitions: to room_dw_church_crumbletower; to
  room_dw_church_fastwater.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_sideclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climb_landingstrip`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_doorAny`, `obj_dw_church_sideclimb`,
  `obj_dw_church_sideclimb_glowclimb`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallaxer`, `obj_ramarker`, `obj_solidblock_soft`,
  `obj_solidblockDark`, `obj_sumarker`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_trueclimbadventure.
- Outgoing transitions: to room_dw_church_trueclimbadventure.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_slidingbookshelf`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bookshelfLanding`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_window_parallax`, `obj_mainchara`,
  `obj_markerAny`, `obj_movingBookshelf`, `obj_overworld_spinningSpade`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_bellsareawest; door from
  room_dw_church_poolsroom2; door from room_dw_church_stairs_topright.
- Outgoing transitions: to room_dw_church_bellsareawest; to
  room_dw_church_poolsroom2; to room_dw_church_stairs_topright; to
  room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_smallbells`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bell_small_playable`, `obj_bellListener`,
  `obj_ch4_DCA08B`, `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_claw.
- Outgoing transitions: to room_dw_church_claw; to room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_solowaterfall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_candlesroom1.
- Outgoing transitions: to room_dw_church_candlesroom1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_stainedglasspreview`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_stairs_stainedglass.
- Outgoing transitions: to room_dw_church_stairs_stainedglass.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_staircase`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCA01`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_staircase`, `obj_dw_church_stairs`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworld_bulletarea_no_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblockDark`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_church_fountainconnection; door from
  room_dw_church_intropiano; door from room_dw_church_knightclimb_post; door
  from room_dw_church_northprophecies.
- Outgoing transitions: to room_dw_church_fountain; to
  room_dw_church_intropiano; to room_dw_church_knightclimb_post; to
  room_dw_church_northprophecies.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_stairs_stainedglass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_window_parallax`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_stainedglasspreview.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_stainedglasspreview.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_stairs_topleft`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cutscene_stairlooper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_legender`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblockDark`, `obj_triggervolume`.
- Incoming transitions: door from room_dw_church_librarybookenemy.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_librarybookenemy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_stairs_topright`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cutscene_stairlooper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_legender`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_botright_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblockDark`, `obj_triggervolume`.
- Incoming transitions: door from room_dw_church_poolsroom1; door from
  room_dw_church_slidingbookshelf.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_church_poolsroom1; to room_dw_church_slidingbookshelf.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_stairs_west_bell`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cutscene_stairlooper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_legender`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_botright_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblockDark`, `obj_triggervolume`.
- Incoming transitions: door from room_dw_church_bellsareawest; door from
  room_dw_church_shelfclimb2.
- Outgoing transitions: to room_dw_church_bellsareawest; to
  room_dw_church_shelfclimb2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_stairspreview`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_stairspreview`, `obj_mainchara`, `obj_markerAny`,
  `obj_parallaxer`, `obj_solidblockDark`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_rightconnect.
- Outgoing transitions: to room_dw_church_rightconnect.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_statueclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_bellhall_east; door from
  room_dw_church_statueclimb_npcroom; door from room_dw_church_statueroom_old.
- Outgoing transitions: to room_dw_church_bellhall_east; to
  room_dw_church_statueclimb_npcroom; to room_dw_church_statueroom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_statueclimb_npcroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_statueclimb.
- Outgoing transitions: to room_dw_church_statueclimb.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_statueroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `ob_rotating_tower_black_bg`, `obj_climbingarea`,
  `obj_cutscene_stairlooper`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_overworld_bulletarea`,
  `obj_rotating_bg_controller`, `obj_rotating_bullet`,
  `obj_rotating_tower_controller`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_candlesroom1; door from
  room_dw_church_poolsroom2; door from room_dw_church_statueclimb.
- Outgoing transitions: to room_dw_church_candlesroom1; to
  room_dw_church_poolsroom2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_statueroom_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climbingarea`, `obj_cutscene_stairlooper`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_candlesroom1; to
  room_dw_church_poolsroom2; to room_dw_church_statueclimb; to
  room_dw_rotating_tower.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_swingingbell`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_bookshelfpuzzle1; to
  room_dw_church_tallbookcases.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_tallbookcases`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climb_door`,
  `obj_climb_marker`, `obj_climbloc`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_church_tallbookcases`, `obj_krmarker`,
  `obj_light_window_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church`, `obj_ramarker`, `obj_solidblockDark`, `obj_sumarker`.
- Incoming transitions: door from room_dw_church_bookshelfpuzzle; door from
  room_dw_church_bookshelfpuzzle_rev; door from room_dw_church_bookshelfpuzzle1;
  door from room_dw_church_lantern2; door from room_dw_church_nwconnect; door
  from room_dw_church_pianopiece_left; door from
  room_dw_church_pianopiece_left_b; door from room_dw_church_pianopiece_right;
  door from room_dw_church_pianopuzzle; door from room_dw_church_secretpiano;
  door from room_dw_church_shelfclimb1; door from
  room_dw_church_slidingbookshelf; door from room_dw_church_smallbells; door
  from room_dw_church_swingingbell.
- Outgoing transitions: to room_dw_church_bookshelfpuzzle_rev; to
  room_dw_church_nwconnect; to room_dw_church_pianopiece_left; to
  room_dw_church_pianopiece_right; to room_dw_church_pianopuzzle; to
  room_dw_church_secretpiano.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_tallbookcases_backup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climb_door`,
  `obj_climb_marker`, `obj_climbloc`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_church_bookshelfpuzzle1; to
  room_dw_church_nwconnect; to room_dw_church_pianopiece_left; to
  room_dw_church_pianopiece_right; to room_dw_church_pianopuzzle.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_tower1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climb_mover`,
  `obj_climb_notsafe`, `obj_climb_spiketile`, `obj_climb_watergenerator`,
  `obj_climbloc`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_church_bellclimb; door from
  room_dw_church_fastwater.
- Outgoing transitions: to room_dw_church_bellclimb; to room_dw_church_climbtut;
  to room_dw_church_fastwater.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_trueclimbadventure`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bell_small_playable`, `obj_camera_clamper`,
  `obj_climb_climbable`, `obj_climb_door`, `obj_climb_marker`,
  `obj_climb_notsafe`, `obj_climb_orb`, `obj_climb_waterbucket`,
  `obj_climb_watergenerator`, `obj_climbloc`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_trueclimbadventure`,
  `obj_dw_church_trueclimbadventure_appeartiles`, `obj_genmarker`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_parallaxer`,
  `obj_solidblockDark`, `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_church_organpuzzle; door from
  room_dw_church_rightconnect; door from room_dw_church_sideclimb.
- Outgoing transitions: to room_dw_church_organpuzzle; to
  room_dw_church_organpuzzle; to room_dw_church_rightconnect; to
  room_dw_church_rightconnect; to room_dw_church_sideclimb.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_turtles`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_turtles`, `obj_genmarker`, `obj_light_area_simple`,
  `obj_light_area_simple_dim`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblockDark`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_bookcase; door from
  room_dw_church_ripplepuzzle; door from room_dw_church_ripplepuzzle_postgers.
- Outgoing transitions: to room_dw_church_bookcase; to
  room_dw_church_lantern_hallway; to room_dw_church_lantern_hallway; to
  room_dw_church_ripplepuzzle.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_waterfallroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_piano_hint`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_glowtile`, `obj_dw_church_waterfallroom`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_ramarker`,
  `obj_slowwalk`, `obj_solidblocksized`, `obj_sumarker`, `obj_trigger`,
  `obj_trigger_interact`.
- Incoming transitions: door from room_dw_church_moneyfountain.
- Outgoing transitions: to room_dw_church_moneyfountain.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_waterfalltearoom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_church_piano_hint`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_waterfalltearoom`,
  `obj_mainchara`, `obj_markerAny`, `obj_parallaxer`, `obj_solidblockDark`,
  `obj_trigger`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_church_moneyfountain.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_church_worshiproom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_worshiproom`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblockDark`, `obj_treasure_room`, `obj_trigger_interact`.
- Incoming transitions: door from room_dw_church_bookshelfpuzzle; door from
  room_dw_church_bookshelfpuzzle_rev; runtime dispatch.
- Outgoing transitions: to room_dw_church_bookshelfpuzzle_rev.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_bellroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_fog`, `obj_dw_churchb_bellroom`, `obj_genmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_escherstaircase; door from
  room_dw_churchb_escherstaircase; door from room_dw_churchb_gallery; door from
  room_dw_churchb_rotatingtower; door from room_dw_churchb_rotatingtower_old;
  door from room_dw_churchb_rotatingtower_tiled.
- Outgoing transitions: to room_dw_churchb_gallery; to
  room_dw_churchb_rotatingtower.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_bookshelf`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_churchb_bookshelf`, `obj_genmarker`,
  `obj_light_window_textureless_mask`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_texturescroller_library`, `obj_tile_oscillate`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_windows.
- Outgoing transitions: to room_dw_churchb_windows.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_darkclimb`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_camera_nudger`,
  `obj_climb_climbable`, `obj_climb_destructableareatrigger`,
  `obj_climb_destructableclimbarea`, `obj_climb_enemykiller`,
  `obj_climb_enemyspawner`, `obj_climb_pathturner`, `obj_climb_setpathenemy`,
  `obj_climb_susie_controller`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_fog`,
  `obj_dw_church_magicalglass_breakable`, `obj_dw_church_window_glow`,
  `obj_dw_churchb_darkclimb`, `obj_dw_churchb_darkclimb_susieSurrounded`,
  `obj_genmarker`, `obj_hsv_shifter`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_proxycandle`, `obj_savepoint`, `obj_solidblocksized`,
  `obj_sumarker`, `obj_texturescroller_dark`, `obj_tile_oscillate`,
  `obj_trigger`, `obj_window_knight_oscillate`.
- Incoming transitions: door from room_dw_churchb_gersonstudy; runtime dispatch.
- Outgoing transitions: to room_dw_churchb_gersonstudy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_darkclimb_scene`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_fog`, `obj_dw_churchb_darkclimb_scene`, `obj_genmarker`,
  `obj_hsv_shifter`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_gallery.
- Outgoing transitions: to room_dw_churchb_gallery.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_escherstaircase`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_churchb_escherstaircase`, `obj_mainchara`,
  `obj_markerAny`, `obj_ramarker`, `obj_solidblock_botleft_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_prophecymaze_old.
- Outgoing transitions: to room_dw_churchb_bellroom; to
  room_dw_churchb_bellroom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_extinguisher`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_churchb_extinguisher`, `obj_genmarker`,
  `obj_hsv_shifter`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_ramarker`, `obj_solidblock_botright_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_nongerson_post; door from
  room_dw_churchb_staircaseintro.
- Outgoing transitions: to room_dw_churchb_nongerson_post; to
  room_dw_churchb_staircaseintro.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_fireplace`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_churchb_fireplace`, `obj_genmarker`, `obj_hsv_shifter`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblock_topleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_gersonstudy.
- Outgoing transitions: to room_dw_churchb_gersonstudy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchb_fountain`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_churchb_staircaseintro; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_churchb_staircaseintro.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_gallery`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_window_glow`, `obj_dw_churchb_gallery`,
  `obj_genmarker`, `obj_hsv_shifter`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_texturescroller`,
  `obj_tile_oscillate`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_bellroom; door from
  room_dw_churchb_darkclimb_scene; door from room_dw_churchb_rotatingtower2.
- Outgoing transitions: to room_dw_churchb_bellroom; to
  room_dw_churchb_darkclimb_scene.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_gersonchase`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_dw_churchb_gersonchase`, `obj_genmarker`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_gersonstudy`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_fog`, `obj_dw_churchb_gersonstudy`, `obj_hsv_shifter`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_savepoint`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_botright_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblockDark`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_darkclimb; door from
  room_dw_churchb_fireplace; door from room_dw_churchb_rotatingtower2; runtime
  dispatch.
- Outgoing transitions: to room_dw_churchb_darkclimb; to
  room_dw_churchb_fireplace.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_library`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bookshelf_destructable`, `obj_camera_clamper`,
  `obj_climb_climbable`, `obj_climb_door`, `obj_climb_marker`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_eye_glow`, `obj_dw_church_fog`,
  `obj_dw_church_remotepianomove`, `obj_dw_church_window_glow`,
  `obj_dw_churchb_library`, `obj_floorTrigger`, `obj_genmarker`,
  `obj_hsv_shifter`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church2`, `obj_parallaxer`, `obj_solid_temp`,
  `obj_solid_temp_edge_maker`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_texturescroller_library`, `obj_tile_oscillate`, `obj_trigger`,
  `obj_trigger_interact`.
- Incoming transitions: door from room_dw_churchb_libraryconnector; door from
  room_dw_churchb_libraryconnector; door from room_dw_churchb_prophecyencounter;
  door from room_dw_churchb_worshiproom.
- Outgoing transitions: to room_dw_churchb_libraryconnector; to
  room_dw_churchb_libraryconnector; to room_dw_churchb_prophecyencounter; to
  room_dw_churchb_worshiproom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_library_alternate`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_bookshelf_destructable`, `obj_climb_climbable`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_doorAny`, `obj_dw_church_remotepianomove`,
  `obj_dw_churchb_library`, `obj_genmarker`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church2`, `obj_solidblocksized`,
  `obj_sumarker`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_churchb_libraryconnector; to
  room_dw_churchb_prophecyencounter; to room_dw_churchb_worshiproom.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_libraryconnector`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_fog`, `obj_dw_churchb_libraryconnector`, `obj_genmarker`,
  `obj_hsv_shifter`, `obj_krmarker`, `obj_layer_floater`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallaxer`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_sumarker`, `obj_texturescroller_library`, `obj_tile_oscillate`,
  `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_library; door from
  room_dw_churchb_library; door from room_dw_churchb_library_alternate; door
  from room_dw_churchb_savepoint.
- Outgoing transitions: to room_dw_churchb_library; to room_dw_churchb_library;
  to room_dw_churchb_savepoint.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_man`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchb_man`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_trigger_interact`.
- Incoming transitions: door from room_dw_churchb_windows.
- Outgoing transitions: to room_dw_churchb_windows.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_moneyfountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_fog`, `obj_dw_church_moneyfountainsprite`,
  `obj_dw_church_waterfall`, `obj_dw_churchb_moneyfountain`, `obj_genmarker`,
  `obj_hsv_shifter`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_churchb_savepoint; runtime dispatch.
- Outgoing transitions: to room_dw_churchb_savepoint.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_nongerson`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dw_churchb_nongerson`,
  `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_nongerson_post`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_ch4_DCB02`,
  `obj_ch4_DCB02_lightning`, `obj_ch4_DCB02_lightning_mask`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_churchb_extinguisher; runtime
  dispatch.
- Outgoing transitions: to room_dw_churchb_extinguisher.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_prophecyencounter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_camera_nudger`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_eye_glow`,
  `obj_dw_church_fog`, `obj_dw_church_window_glow`,
  `obj_dw_churchb_prophecyencounter`, `obj_genmarker`, `obj_hsv_shifter`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_parallaxer`,
  `obj_solidblock_botleft_dark`, `obj_solidblock_topright_dark`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_texturescroller`,
  `obj_tile_oscillate`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_library; door from
  room_dw_churchb_library_alternate; door from room_dw_churchb_ripple1; door
  from room_dw_churchb_ripplepost.
- Outgoing transitions: to room_dw_churchb_library; to
  room_dw_churchb_ripplepost.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_prophecymaze`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchb_prophecymaze`, `obj_genmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_ramarker`, `obj_solidblocksized`, `obj_treasure_room`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_prophecymaze; door from
  room_dw_churchb_prophecymaze.
- Outgoing transitions: to room_dw_churchb_prophecymaze; to
  room_dw_churchb_prophecymaze.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_prophecymaze_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_churchb_prophecymaze`, `obj_genmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_trigger`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_churchb_escherstaircase; to
  room_dw_churchb_rotatingtower2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_ripple1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_window_glow`, `obj_dw_churchb_ripple1`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_staircaseintro.
- Outgoing transitions: to room_dw_churchb_prophecyencounter; to
  room_dw_churchb_staircaseintro.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_ripplepost`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_fog`, `obj_dw_church_window_glow`, `obj_dw_churchb_ripplepost`,
  `obj_hsv_shifter`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church2`, `obj_parallaxer`, `obj_solidblocksized`,
  `obj_texturescroller`, `obj_tile_oscillate`.
- Incoming transitions: door from room_dw_churchb_prophecyencounter; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_church_gersonstudy; to
  room_dw_churchb_prophecyencounter; to room_dw_churchb_staircaseintro.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_rotatingtower`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_camera_nudger`, `obj_climb_climbable`,
  `obj_climb_susie_controller`, `obj_climb_waterbucket`,
  `obj_climb_watergenerator`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_eye_glow`,
  `obj_dw_church_fog`, `obj_dw_church_window_glow`,
  `obj_dw_churchb_rotatingtower`, `obj_genmarker`, `obj_hsv_shifter`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_dw_church2`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_controller_new`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_texturescroller`, `obj_tile_oscillate`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_bellroom; door from
  room_dw_churchb_savepoint; door from room_dw_churchb_windows.
- Outgoing transitions: to room_dw_churchb_bellroom; to
  room_dw_churchb_savepoint; to room_dw_churchb_windows.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_rotatingtower_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_camera_nudger`, `obj_climb_climbable`,
  `obj_climb_mover`, `obj_climb_orb`, `obj_climb_pathturner`,
  `obj_climb_setpathenemy`, `obj_climb_waterbucket`, `obj_climb_watergenerator`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_doorAny`, `obj_dw_churchb_rotatingtower`,
  `obj_genmarker`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_dw_church2`, `obj_ramarker`, `obj_rotating_bg_controller_new`,
  `obj_rotating_bullet_new`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_churchb_bellroom; to
  room_dw_churchb_savepoint.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_rotatingtower_tiled`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_camera_nudger`, `obj_climb_climbable`,
  `obj_climb_susie_controller`, `obj_climb_waterbucket`,
  `obj_climb_watergenerator`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_church_eye_glow`,
  `obj_dw_church_fog`, `obj_dw_church_window_glow`,
  `obj_dw_churchb_rotatingtower`, `obj_genmarker`, `obj_hsv_shifter`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_dw_church2`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_controller_new`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_texturescroller`, `obj_tile_oscillate`, `obj_trigger`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_churchb_bellroom; to
  room_dw_churchb_savepoint; to room_dw_churchb_windows.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_rotatingtower2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_camera_nudger`,
  `obj_climb_climbable`, `obj_climb_enemykiller`, `obj_climb_enemyspawner`,
  `obj_climb_mover`, `obj_climb_orb`, `obj_climb_pathturner`,
  `obj_climb_waterbucket`, `obj_climb_watergenerator`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchb_rotatingtower2`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church2`, `obj_rotating_bg_controller_new`,
  `obj_rotating_bullet_new`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`, `obj_sumarker`.
- Incoming transitions: door from room_dw_churchb_prophecymaze_old.
- Outgoing transitions: to room_dw_churchb_gallery; to
  room_dw_churchb_gersonstudy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_savepoint`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_fog`, `obj_dw_churchb_savepoint`,
  `obj_hsv_shifter`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_dw_church2`,
  `obj_savepoint`, `obj_solidblock_botleft_dark`,
  `obj_solidblock_botright_dark`, `obj_solidblock_topleft_dark`,
  `obj_solidblock_topright_dark`, `obj_solidblockDark`, `obj_texturescroller`,
  `obj_tile_oscillate`.
- Incoming transitions: door from room_dw_churchb_libraryconnector; door from
  room_dw_churchb_moneyfountain; door from room_dw_churchb_rotatingtower; door
  from room_dw_churchb_rotatingtower_old; door from
  room_dw_churchb_rotatingtower_tiled.
- Outgoing transitions: to room_dw_churchb_libraryconnector; to
  room_dw_churchb_moneyfountain; to room_dw_churchb_rotatingtower.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_staircaseintro`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchb_staircaseintro`, `obj_genmarker`, `obj_hsv_shifter`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_ramarker`,
  `obj_savepoint`, `obj_solidblocksized`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_extinguisher; door from
  room_dw_churchb_fountain; door from room_dw_churchb_ripple1; door from
  room_dw_churchb_ripplepost.
- Outgoing transitions: to room_dw_churchb_extinguisher; to
  room_dw_churchb_fountain; to room_dw_churchb_ripple1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_windows`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchb_windows`, `obj_genmarker`, `obj_hsv_shifter`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_solidenemy_2`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchb_bookshelf; door from
  room_dw_churchb_man; door from room_dw_churchb_rotatingtower; door from
  room_dw_churchb_rotatingtower_tiled; door from
  room_dw_churchc_angelprophecy_encounter.
- Outgoing transitions: to room_dw_churchb_bookshelf; to room_dw_churchb_man; to
  room_dw_churchb_rotatingtower.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchb_worshiproom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_fog`, `obj_dw_church_worshiproom`, `obj_hsv_shifter`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblock_botleft_dark`,
  `obj_solidblock_topleft_dark`, `obj_solidblockDark`, `obj_treasure_room`,
  `obj_trigger_interact`.
- Incoming transitions: door from room_dw_churchb_library; door from
  room_dw_churchb_library_alternate; runtime dispatch.
- Outgoing transitions: to room_dw_churchb_library.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_angelprophecy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_angelprophecy`, `obj_genmarker`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_proxycandle`, `obj_ramarker`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_texturemask`,
  `obj_texturescroller_prophecy`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchc_angelprophecy_encounter.
- Outgoing transitions: to room_dw_churchc_angelprophecy_encounter.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_angelprophecy_encounter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_angelprophecy_encounter`, `obj_genmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church3`, `obj_proxycandle`,
  `obj_solidblocksized`, `obj_texturemask`, `obj_texturescroller_prophecy`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_churchc_angelprophecy; door from
  room_dw_churchc_dodge; runtime dispatch.
- Outgoing transitions: to room_dw_churchb_windows; to
  room_dw_churchc_angelprophecy; to room_dw_churchc_dodge.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_darkswords`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkswordthrower`,
  `obj_doorAny`, `obj_dw_churchc_darkswords`, `obj_mainchara`, `obj_markerAny`,
  `obj_overworld_bulletarea_no_dark`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_churchc_finalclimb; door from
  room_dw_churchc_prepretitan.
- Outgoing transitions: to room_dw_churchc_finalclimb; to
  room_dw_churchc_prepretitan.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_dodge`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_church_magicalglass_breakable`, `obj_dw_churchc_dodge`,
  `obj_dw_churchc_dodge_trigger`, `obj_layershader`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church3`, `obj_overworld_bulletarea`,
  `obj_parallaxer`, `obj_solidblocksized`, `obj_texturemask`,
  `obj_texturescroller_prophecy`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchc_angelprophecy_encounter; door
  from room_dw_churchc_encounter1; door from room_dw_churchc_encounter2.
- Outgoing transitions: to room_dw_churchc_angelprophecy_encounter; to
  room_dw_churchc_encounter1; to room_dw_churchc_encounter2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_encounter1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_bluebook_straight`, `obj_dw_churchc_encounter1`,
  `obj_genmarker`, `obj_krmarker`, `obj_layershader`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church3`, `obj_parallaxer`,
  `obj_proxycandle`, `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_texturemask`, `obj_texturescroller_prophecy`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchc_dodge; door from
  room_dw_churchc_prophecies; door from room_dw_churchc_prophecies_backup; door
  from room_dw_churchc_superprophecies.
- Outgoing transitions: to room_dw_churchc_dodge; to room_dw_churchc_prophecies;
  to room_dw_churchc_superprophecies.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_encounter2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_glowtile`, `obj_dw_church_organikchaser`,
  `obj_dw_churchc_encounter2`, `obj_layershader`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallaxer`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_churchc_dodge; door from
  room_dw_churchc_ripplesneak_poc; door from room_dw_churchc_slidingpiano; door
  from room_dw_churchc_treasurechest.
- Outgoing transitions: to room_dw_churchc_dodge; to
  room_dw_churchc_slidingpiano; to room_dw_churchc_treasurechest.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_final_prophecy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCC03`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_final_prophecy`, `obj_hsv_shifter`, `obj_layershader`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_churchc_titandefeated.
- Outgoing transitions: to room_cc_fountain; to room_dw_churchc_titandefeated.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_finalclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_finalclimb`, `obj_layershader`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallaxer`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_churchc_darkswords; door from
  room_dw_churchc_savepoint.
- Outgoing transitions: to room_dw_churchc_darkswords; to
  room_dw_churchc_savepoint.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_insidetitan`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dw_churchc_insidetitan`,
  `obj_mainchara`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_prepretitan`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_churchc_prepretitan`, `obj_mainchara`, `obj_markerAny`,
  `obj_parallaxer`, `obj_savepoint`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_churchc_darkswords; door from
  room_dw_churchc_pretitan.
- Outgoing transitions: to room_dw_churchc_darkswords; to
  room_dw_churchc_pretitan.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_pretitan`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCC01`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_pretitan`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_churchc_prepretitan.
- Outgoing transitions: to room_dw_churchc_prepretitan.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_prophecies`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climb_destructableclimbarea`, `obj_climb_landingstrip`,
  `obj_climb_mover`, `obj_climb_watergenerator`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_doorAny`, `obj_dw_churchc_prophecies`, `obj_floorTrigger`,
  `obj_genmarker`, `obj_krmarker`, `obj_layershader`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallaxer`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_sumarker`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_churchc_encounter1.
- Outgoing transitions: to room_dw_churchc_encounter1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_prophecies_backup`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climb_landingstrip`, `obj_climb_mover`, `obj_climb_watergenerator`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_churchc_prophecies`, `obj_genmarker`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_sumarker`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_churchc_encounter1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_ripplesneak_poc`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_waterfallchaser_churchc`, `obj_dw_churchc_ripplesneak_poc`,
  `obj_lightsource_shrinking`, `obj_lightsource_static`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_dw_church3`, `obj_overworld_bulletarea`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: to room_dw_churchc_encounter2; to
  room_dw_churchc_slidingpiano.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_savepoint`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_savepoint`, `obj_dw_churchc_savepoint_judgmentbell`,
  `obj_layershader`, `obj_mainchara`, `obj_markerAny`, `obj_proxycandle`,
  `obj_savepoint`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_churchc_finalclimb; door from
  room_dw_churchc_slidingpiano.
- Outgoing transitions: to room_dw_churchc_finalclimb; to
  room_dw_churchc_slidingpiano.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_slidingpiano`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bookshelf_destructable`, `obj_camera_clamper`,
  `obj_church_piano_hint`, `obj_climb_cloudspeedcontroller`,
  `obj_cloud_controller_new`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_church_glowtile`, `obj_dw_church_remotepianomove`,
  `obj_dw_churchc_slidingpiano`, `obj_genmarker`, `obj_krmarker`,
  `obj_layershader`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_dw_church3`,
  `obj_parallaxer`, `obj_proxycandle`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_sumarker`.
- Incoming transitions: door from room_dw_churchc_encounter2; door from
  room_dw_churchc_ripplesneak_poc; door from room_dw_churchc_savepoint.
- Outgoing transitions: to room_dw_churchc_encounter2; to
  room_dw_churchc_savepoint.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_superprophecies`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_superprophecies`, `obj_genmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallaxer`, `obj_savepoint`, `obj_solidblockDark`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_church_knightclimb_post; door from
  room_dw_churchc_encounter1.
- Outgoing transitions: to room_dw_church_knightclimb_post; to
  room_dw_churchc_encounter1.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb1`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_animationmarker`, `obj_climb_camera_nudger`,
  `obj_climb_destructableareatrigger`, `obj_climb_destructableclimbarea`,
  `obj_climb_evilgrowth`, `obj_climb_explosion`, `obj_climb_eyewaterenemy`,
  `obj_climb_immobileeye`, `obj_climb_marker`, `obj_climb_pathturner`,
  `obj_climb_setpathenemy`, `obj_climb_titan_kris_throw_off_sequence`,
  `obj_climbloc`, `obj_darkcontroller`, `obj_dw_churchc_titanclimb1`,
  `obj_mainchara`, `obj_musicer_dw_titan_climb`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_animation`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb1_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_animationmarker`,
  `obj_climb_destructableareatrigger`, `obj_climb_destructableclimbarea`,
  `obj_climb_enemyspawner`, `obj_climb_explosion`, `obj_climb_eyewaterenemy`,
  `obj_climb_immobileeye`, `obj_climb_notsafe`, `obj_climb_setpathenemy`,
  `obj_climb_titan_kris_throw_off_sequence`, `obj_climbloc`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_markerAny`, `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_animation`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb1_post`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_dw_churchc_titanclimb1_post`, `obj_mainchara`, `obj_solidblockDark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb1_tiled`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_animationmarker`, `obj_climb_camera_nudger`,
  `obj_climb_destructableareatrigger`, `obj_climb_destructableclimbarea`,
  `obj_climb_evilgrowth`, `obj_climb_explosion`, `obj_climb_eyewaterenemy`,
  `obj_climb_immobileeye`, `obj_climb_marker`, `obj_climb_pathturner`,
  `obj_climb_setpathenemy`, `obj_climb_titan_kris_throw_off_sequence`,
  `obj_climbloc`, `obj_darkcontroller`, `obj_dw_churchc_titanclimb1`,
  `obj_mainchara`, `obj_musicer_dw_titan_climb`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_animation`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_animationmarker`, `obj_climb_camera_nudger`,
  `obj_climb_cloudspeedcontroller`, `obj_climb_destructableareatrigger`,
  `obj_climb_enemykiller`, `obj_climb_enemyspawner`, `obj_climb_explosion`,
  `obj_climb_eyewaterenemy`, `obj_climb_immobileeye`, `obj_climb_marker`,
  `obj_climb_notsafe`, `obj_climb_pathturner`, `obj_climb_susie_controller`,
  `obj_climb_titan_kris_throw_off_sequence`, `obj_cloud_controller_new`,
  `obj_darkcontroller`, `obj_dw_churchc_titanclimb2`, `obj_genmarker`,
  `obj_mainchara`, `obj_musicer_dw_titan_climb`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_animation`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb2_old`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_animationmarker`, `obj_climb_camera_nudger`,
  `obj_climb_cloudspeedcontroller`, `obj_climb_destructableareatrigger`,
  `obj_climb_destructableclimbarea`, `obj_climb_enemyspawner`,
  `obj_climb_explosion`, `obj_climb_eyewaterenemy`, `obj_climb_immobileeye`,
  `obj_climb_notsafe`, `obj_climb_pathturner`, `obj_climb_setpathenemy`,
  `obj_climbloc`, `obj_climbstartertrig`, `obj_cloud_controller_new`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_markerAny`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_animation`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb2_old2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_animationmarker`, `obj_climb_camera_nudger`,
  `obj_climb_cloudspeedcontroller`, `obj_climb_destructableareatrigger`,
  `obj_climb_explosion`, `obj_climb_eyewaterenemy`, `obj_climb_immobileeye`,
  `obj_climb_marker`, `obj_climb_notsafe`, `obj_climb_pathturner`,
  `obj_climb_setpathenemy`, `obj_climb_susie_controller`,
  `obj_climb_titan_kris_throw_off_sequence`, `obj_cloud_controller_new`,
  `obj_darkcontroller`, `obj_dw_churchc_titanclimb2`, `obj_genmarker`,
  `obj_mainchara`, `obj_musicer_dw_titan_climb`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_animation`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb2_post`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cloud_controller_new`, `obj_darkcontroller`,
  `obj_dw_churchc_titanclimb2_post`, `obj_genmarker`, `obj_mainchara`,
  `obj_parallaxer`, `obj_solidblockDark`, `obj_solidblocksized_alt`,
  `obj_titan_layer_floater`, `obj_trigger`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titanclimb2_tiled`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_animationmarker`, `obj_climb_camera_nudger`,
  `obj_climb_cloudspeedcontroller`, `obj_climb_destructableareatrigger`,
  `obj_climb_enemykiller`, `obj_climb_enemyspawner`, `obj_climb_explosion`,
  `obj_climb_eyewaterenemy`, `obj_climb_immobileeye`, `obj_climb_marker`,
  `obj_climb_notsafe`, `obj_climb_pathturner`, `obj_climb_susie_controller`,
  `obj_climb_titan_kris_throw_off_sequence`, `obj_cloud_controller_new`,
  `obj_darkcontroller`, `obj_dw_churchc_titanclimb2`, `obj_genmarker`,
  `obj_mainchara`, `obj_musicer_dw_titan_climb`,
  `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_animation`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_titandefeated`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCC02`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblock_topleft_dark`,
  `obj_solidblock_topright_dark`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_churchc_final_prophecy; runtime
  dispatch.
- Outgoing transitions: to room_dw_churchc_final_prophecy.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_churchc_treasurechest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_churchc_treasurechest`, `obj_genmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_churchc_encounter2.
- Outgoing transitions: to room_dw_churchc_encounter2.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_ralsei_castle_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_cauldron_glow`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorW`, `obj_mainchara`, `obj_markerB`, `obj_markerw`,
  `obj_markerX`, `obj_npc_room_animated`, `obj_readable_room1`,
  `obj_room_castle_1f`, `obj_room_castle_1f_cake`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorB from room_dw_ralsei_castle_2f
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_ralsei_castle_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerAny`, `obj_markerX`,
  `obj_room_castle_2f`, `obj_soliddark`.
- Incoming transitions: door from room_dw_castle_rooms_kris; door from
  room_dw_castle_rooms_kris_susie; door from room_dw_castle_rooms_kris_susie;
  door from room_dw_castle_rooms_susie; door from room_dw_ralsei_castle_3f;
  enabled placed obj_doorA from room_dw_ralsei_castle_1f resolves room_goto_next
  via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: to room_dw_castle_rooms_kris_susie; to
  room_dw_castle_rooms_kris_susie; to room_dw_ralsei_castle_3f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_ralsei_castle_3f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_PDC06A`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_darkcastle`,
  `obj_room_castle_3f`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_rooms_queen; door from
  room_dw_castle_rooms_ralsei; door from room_dw_castle_rooms_tenna; door from
  room_dw_ralsei_castle_2f.
- Outgoing transitions: to room_dw_castle_rooms_queen; to
  room_dw_castle_rooms_ralsei; to room_dw_castle_rooms_tenna; to
  room_dw_ralsei_castle_2f.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_ralsei_castle_front`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castle_torch`, `obj_darkcontroller`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerX`,
  `obj_room_castle_front`, `obj_soliddark`.
- Incoming transitions: enabled placed obj_doorA from room_dw_castle_town
  resolves room_goto_next via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_rhythm`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_rhythmgame`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_rhythm_countdown`

- Area: Rhythm subsystem.
- Runtime role/status: border/tension handling includes this countdown room; no
  ingress transition verified; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_room_rhythm_countdown`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_rhythm_empty`

- Area: Rhythm subsystem.
- Runtime role/status: empty rhythm staging/template asset; no runtime dispatch
  verified; uncertain-no-ingress.
- Important controllers: `none placed or creation-code-created`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_rotating_tower`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climbingarea`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_markerAny`, `obj_overworld_bulletarea`,
  `obj_rotating_bg_controller`, `obj_rotating_bullet`,
  `obj_rotating_tower_controller`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_church_statueroom_old.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_dw_titan_tower_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climbingarea`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_markerAny`, `obj_rotating_bg_controller`,
  `obj_rotating_tower_controller`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_ed`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_credits_ch4`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_empty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 4: `room_flowershop_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorX`, `obj_flowershop_event`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorB from room_flowershop_2f
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_flowershop_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_flowershop_event`, `obj_mainchara`,
  `obj_markerA`, `obj_npc_sign`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_flowershop_1f
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_gameover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_gameover_init`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_gersonbattleroomtest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_gerson_windowbg`,
  `obj_mainchara`, `obj_solidblock`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_gif_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_sprite_catalog`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_gms_debug_failsafe`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_gamecontroller`, `obj_gms_debug_failsafe`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `room_GMS2_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_soliddark`, `obj_swordarea`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_graveyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_doorB`,
  `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerA`, `obj_markerX`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_sur`, `obj_town_event`, `obj_town_graveyard`.
- Incoming transitions: enabled placed obj_doorA from room_town_church resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_hospital_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_mainchara`,
  `obj_markerA`, `obj_markerAny`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_hospital_hallway`, `obj_solidblock`, `obj_trigger`.
- Incoming transitions: enabled placed obj_doorA from room_hospital_lobby
  resolves room_goto_next via scr_get_room_by_id asset order; enabled placed
  obj_doorB from room_hospital_rudy resolves room_goto_previous via
  scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_hospital_lobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorW`, `obj_mainchara`,
  `obj_markerB`, `obj_markerw`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorB from room_hospital_hallway
  resolves room_goto_previous via scr_get_room_by_id asset order; runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_hospital_room2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_room_town_hospital_room2`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_hospital_rudy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_npc_rudy`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_hospital`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorA from room_hospital_hallway
  resolves room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `ROOM_INITIALIZE`

- Area: Bootstrap.
- Runtime role/status: runtime initialization room; bootstrap.
- Important controllers: `obj_gamecontroller`, `obj_initializer2`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 4: `room_insidecloset`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_intro_ch4`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_intro_ch4`.
- Incoming transitions: runtime variable dispatch to room_intro_ch4; runtime
  variable dispatch to room_intro_ch4.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_krishallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_doorC`, `obj_hallway_mirror`,
  `obj_mainchara`, `obj_markerA`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`, `obj_solidlong`.
- Incoming transitions: enabled placed obj_doorA from room_krisroom resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_krisroom`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch4_PDC01D`, `obj_doorA`, `obj_krisroom`,
  `obj_mainchara`, `obj_markerB`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_savepoint`, `obj_solidblock`.
- Incoming transitions: enabled placed obj_doorB from room_krishallway resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_krisroom_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_LWF04`, `obj_ch4_LWF04_wagon`,
  `obj_krisroom_dark`, `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_legend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_legend`.
- Incoming transitions: runtime variable dispatch to room_legend; runtime
  variable dispatch to room_legend.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_legend_neo`

- Area: Development.
- Runtime role/status: Sunkus-key debug Legend destination from obj_mainchara
  input; uncertain-no-ingress.
- Important controllers: `obj_legend_neo`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lerptest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_lerptest`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_library`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorW`, `obj_doorX`,
  `obj_mainchara`, `obj_markert`, `obj_markerw`, `obj_markerX`,
  `obj_npc_facing`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_town_library`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lightworldTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_camera_nudger`, `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_church_choir`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworldc`, `obj_room_church_choir`,
  `obj_solidblockLight`.
- Incoming transitions: door from room_lw_church_entrance; door from
  room_lw_church_main.
- Outgoing transitions: to room_lw_church_entrance; to room_lw_church_main.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_church_entrance`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_DCA13`, `obj_ch4_DCA15`, `obj_ch4_DCB03`,
  `obj_ch4_PDC02`, `obj_church_entrance`, `obj_church_entrance_foreground`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_overworldc`,
  `obj_solidblockLight`.
- Incoming transitions: door from room_lw_church_choir; door from
  room_lw_church_main; door from room_lw_church_office; door from
  room_town_church; runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_lw_church_choir; to room_lw_church_main; to
  room_lw_church_office; to room_town_church.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_church_main`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch4_LWF01`, `obj_ch4_PDC03`,
  `obj_ch4_PDC03_catty_preach`, `obj_ch4_PDC03_choir_song`, `obj_ch4_PDC04`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_overworldc`,
  `obj_room_church_main`, `obj_solidblockLight`, `obj_sul`, `obj_sur`.
- Incoming transitions: door from room_lw_church_choir; door from
  room_lw_church_entrance; runtime dispatch.
- Outgoing transitions: to room_lw_church_choir; to room_lw_church_entrance.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_church_office`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch4_DCA14`, `obj_doorAny`,
  `obj_mainchara`, `obj_markerAny`, `obj_overworldc`, `obj_room_church_office`,
  `obj_solidblockLight`.
- Incoming transitions: door from room_lw_church_entrance.
- Outgoing transitions: to room_lw_church_entrance.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_computer_lab`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_conbini`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorw_musfade`,
  `obj_mainchara`, `obj_markerv`, `obj_musicer_conbini`, `obj_npc_conbini`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_icee_pizza`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorW`, `obj_mainchara`,
  `obj_markert`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_soliddark`, `obj_town_pizza`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_library_upstairs`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorW`, `obj_mainchara`, `obj_markert`,
  `obj_npc_library_upstairs`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdl_dark`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_basement`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_homealone_basement_boombox`, `obj_homealone_bell`,
  `obj_homealone_solid`, `obj_homealone_vent_hidden`, `obj_mainchara`,
  `obj_noellehouse_basement`, `obj_overworldc`.
- Incoming transitions: creation context room door and placed
  obj_noellehouse_basement drive the basement sequence.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: gates the sequence on scr\_sideb\_active() and global.plot == 63,
  then advances plot to 65.

### Chapter 4: `room_lw_noellehouse_bathroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_PDC14A_bathroom`, `obj_doorAny`,
  `obj_homealone_bathroom`, `obj_homealone_solid`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_markerAny`,
  `obj_noellehouse_bathroom`, `obj_overworldc`, `obj_solidblockLight`,
  `obj_sul`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_lw_noellehouse_main.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_closet`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch4_PDC10C`, `obj_doorAny`,
  `obj_homealone_solid`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_markerAny`,
  `obj_overworldc`, `obj_solidblockLight`.
- Incoming transitions: door from room_lw_noellehouse_main; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_lw_noellehouse_main.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_dess`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch4_PDC10A`, `obj_doorAny`,
  `obj_homealone_dess_closet_controller`, `obj_homealone_solid`,
  `obj_homealone_vent_hidden`, `obj_homealone_vent_overlay`, `obj_mainchara`,
  `obj_markerAny`, `obj_noellehouse_dess`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblockLight`.
- Incoming transitions: door from room_lw_noellehouse_main.
- Outgoing transitions: to room_lw_noellehouse_main.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_keyroom`

- Area: Noelle house.
- Runtime role/status: Key-room route destination reached by the house door
  controller; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_overworldc`, `obj_solidblockLight`.
- Incoming transitions: placed obj_doorAny; Noelle-house door dispatch context
  runtime controller.
- Outgoing transitions: to room_lw_noellehouse_main.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_kitchen`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorAny`,
  `obj_homealone_kitchen`, `obj_homealone_kitchen_phone`, `obj_homealone_piano`,
  `obj_homealone_solid`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_markerAny`,
  `obj_overworldc`, `obj_readable_room1`, `obj_savepoint`,
  `obj_solidblockLight`.
- Incoming transitions: door from room_lw_noellehouse_main.
- Outgoing transitions: to room_lw_noellehouse_main.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_main`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorAny`,
  `obj_homealone_bell`, `obj_homealone_solid`, `obj_homealone_sul`,
  `obj_homealone_sur`, `obj_homealone_treat_catcher`,
  `obj_homealone_vent_hidden`, `obj_homealone_vent_overlay`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_noellehouse`, `obj_noellehouse_main`,
  `obj_overworldc`, `obj_readable_room1`, `obj_sdl`, `obj_sdr`,
  `obj_solidblockLight`, `obj_sul`, `obj_sur`.
- Incoming transitions: door from room_lw_noellehouse_bathroom; door from
  room_lw_noellehouse_closet; door from room_lw_noellehouse_dess; door from
  room_lw_noellehouse_keyroom; door from room_lw_noellehouse_kitchen; door from
  room_lw_noellehouse_noelle; door from room_town_noellehouse; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_lw_noellehouse_closet; to
  room_lw_noellehouse_dess; to room_lw_noellehouse_kitchen; to
  room_lw_noellehouse_noelle; to room_town_noellehouse.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_noelle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch4_PDC14A_noelle`,
  `obj_doorAny`, `obj_homealone_solid`, `obj_homealone_sul`,
  `obj_homealone_vent_hidden`, `obj_homealone_vent_overlay`, `obj_mainchara`,
  `obj_markerAny`, `obj_noellehouse_noelle`, `obj_overworldc`, `obj_sdl`,
  `obj_sdr`, `obj_solidblockLight`.
- Incoming transitions: door from room_lw_noellehouse_main.
- Outgoing transitions: to room_lw_noellehouse_main.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_north`

- Area: Noelle house.
- Runtime role/status: North home-invasion route room driven by
  obj_noellehouse_north; verified production reachable.
- Important controllers: `obj_homealone_solid`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_noellehouse_north`,
  `obj_overworldc`.
- Incoming transitions: creation context room door targets
  room_lw_noellehouse_north; placed obj_noellehouse_north.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_vents_east`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_homealone_solid`, `obj_homealone_vent_airflow`,
  `obj_homealone_vent_airflow_controller`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_musicer_gen`,
  `obj_overworldc`.
- Incoming transitions: door context room door targets
  room_lw_noellehouse_vents_east.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_vents_north`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_homealone_solid`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_musicer_gen`,
  `obj_overworldc`.
- Incoming transitions: door context room door targets
  room_lw_noellehouse_vents_north.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_vents_north_west`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_homealone_solid`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_musicer_gen`,
  `obj_overworldc`.
- Incoming transitions: door context room door targets
  room_lw_noellehouse_vents_north_west.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_vents_south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_homealone_solid`, `obj_homealone_vent_airflow`,
  `obj_homealone_vent_airflow_controller`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_musicer_gen`,
  `obj_overworldc`.
- Incoming transitions: door context room door targets
  room_lw_noellehouse_vents_south.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_noellehouse_vents_west`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_homealone_solid`, `obj_homealone_vent_hidden`,
  `obj_homealone_vent_overlay`, `obj_mainchara`, `obj_musicer_gen`,
  `obj_overworldc`.
- Incoming transitions: door context room door targets
  room_lw_noellehouse_vents_west.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_lw_police`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_mainchara`, `obj_markerv`,
  `obj_npc_police`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_town_south.
- Conditions: No additional condition verified.

### Chapter 4: `room_overworld_darkmaku_blocks`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_dw_church_pushableshelf_3x3`, `obj_heightfloor_darklight`,
  `obj_lightsource_traveling`, `obj_mainchara`, `obj_overworld_danmaku_spawner`,
  `obj_overworld_darkness_bulletarea`, `obj_solidblocksized`, `obj_solidenemy`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_overworld_darkmaku_ring`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_lightsource`, `obj_mainchara`, `obj_overworld_bullet_killer`,
  `obj_overworld_bulletarea`, `obj_overworld_danmaku_spawner`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_overworld_darkmakumaze`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_lightsource_traveling`, `obj_mainchara`, `obj_overworld_bulletarea`,
  `obj_overworld_danmaku_spawner`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_overworldBulletEnemyTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_overworld_bulletarea`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_overworldDarknessBulletTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_darkness_overlay`,
  `obj_lightsource`, `obj_mainchara`, `obj_moving_lightsource`,
  `obj_overworld_bullet_killer`, `obj_overworld_bulletarea`,
  `obj_overworld_darkness_bullet_maker`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_rhythmgame_editor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_rhythmgame_editor`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_ripple_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_church_old_man_ripple`, `obj_church_ripple_area`,
  `obj_church_ripple_area_manager`, `obj_darkcontroller`,
  `obj_darkness_overlay`, `obj_lightsource`, `obj_mainchara`, `obj_roomglow`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_rotating_tower_new_example`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climb_enemyspawner`,
  `obj_climb_eyewaterenemy`, `obj_climb_notsafe`, `obj_climb_spiketile`,
  `obj_climb_wall`, `obj_climb_waterbucket`, `obj_climb_watergenerator`,
  `obj_climbloc`, `obj_climbstartertrig`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_markerAny`, `obj_rotating_bg_controller_new`, `obj_rotating_bullet_new`,
  `obj_rotating_tower_controller_new`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_rotating_tower_new_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climb_enemyspawner`,
  `obj_climb_notsafe`, `obj_climb_spiketile`, `obj_climb_wall`,
  `obj_climb_waterbucket`, `obj_climbloc`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_markerAny`,
  `obj_rotating_bg_controller_new`, `obj_rotating_tower_controller_new`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_school_unusedroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_unusedclassevent`.
- Incoming transitions: non-production unused classroom; excluded from ordered
  adjacency and only referenced by unused/fountain cleanup/readable-room
  compatibility code.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_schooldoor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkdoor`, `obj_doorC`, `obj_doorD`,
  `obj_lw_rain_indoor_ambience`, `obj_mainchara`, `obj_markerC`, `obj_markerD`,
  `obj_markerX`, `obj_musicer_town`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_schooldoor`, `obj_solidblock`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_schoollobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorAny`, `obj_doorB`, `obj_doorC`,
  `obj_lw_rain_indoor_ambience`, `obj_mainchara`, `obj_markerA`, `obj_markerB`,
  `obj_markerD`, `obj_markerX`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_schoollobby`, `obj_solidblock`, `obj_sul`.
- Incoming transitions: door from room_town_school; enabled placed obj_doorA
  from room_torielclass resolves room_goto_next via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_town_school.
- Conditions: No additional condition verified.

### Chapter 4: `room_shapetest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`, `obj_shapetest`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_shop_music`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop_music`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_shop1`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop1`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_sound_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_soundtester`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_sprite_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_spritecomparer`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_test_climb_0001`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climb_enemyspawner`,
  `obj_climb_eyewaterenemy`, `obj_climb_immobileeye`, `obj_climb_interact`,
  `obj_climb_kris`, `obj_climb_orb`, `obj_climb_pathturner`,
  `obj_climb_setpathenemy`, `obj_darkcontroller`, `obj_mainchara`,
  `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_test_climb_cameratest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climb_hazardtile`,
  `obj_climb_kris`, `obj_climb_watergenerator`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_test_climb_enterexit`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climbloc`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_solidblockDark`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_test_climb_new`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obJ_climb_bulletspawner`, `obj_climb_climbable`,
  `obj_climb_enemy`, `obj_climb_hazardtile`, `obj_climb_kris`,
  `obj_climb_susie`, `obj_climb_susie_controller`, `obj_darkcontroller`,
  `obj_genmarker`, `obj_mainchara`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_test_climb_new2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climb_hazardtile`,
  `obj_climb_kris`, `obj_climb_watergenerator`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_test_pianoGimmick`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_dw_church_organ`,
  `obj_mainchara`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_test_remotePiano`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_dw_church_remote_piano`,
  `obj_mainchara`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_title_placeholder`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_title_placeholder`.
- Incoming transitions: runtime variable dispatch to room_title_placeholder.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 4: `room_torbathroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_sur`, `obj_town_event`.
- Incoming transitions: enabled placed obj_doorA from room_torhouse resolves
  room_goto_next via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_torhouse`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch4_LWF03`, `obj_ch4_PDC01B`, `obj_ch4_PDC01C`,
  `obj_doorA`, `obj_doorD`, `obj_doorX_musfade`, `obj_lw_rain_indoor_ambience`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_markerX`,
  `obj_musicer_torhouse`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_room_torhouse`, `obj_sdl`, `obj_sdr`,
  `obj_solidblock`, `obj_solidlong`, `obj_sul`, `obj_sur`.
- Incoming transitions: enabled placed obj_doorB from room_torbathroom resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_torielclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_mainchara`,
  `obj_markerB`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`,
  `obj_torielclass_event`.
- Incoming transitions: enabled placed obj_doorB from room_schoollobby resolves
  room_goto_previous via scr_get_room_by_id asset order.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_torroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_apartments`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_church`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_ch4_LWF02`,
  `obj_ch4_PDC05`, `obj_ch4_PDC16`, `obj_church_event`, `obj_doorA`,
  `obj_doorAny`, `obj_doorD`, `obj_doorX`, `obj_lw_rain_dryzone`,
  `obj_lw_rain_effect`, `obj_lw_town_sideb`, `obj_mainchara`, `obj_markerAny`,
  `obj_markerB`, `obj_markerC`, `obj_markerD`, `obj_markerX`,
  `obj_musicer_town`, `obj_npc_room`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_room_town_church`, `obj_sdl`, `obj_sdr`, `obj_solidblock`,
  `obj_solidblockLight`, `obj_soliddark`.
- Incoming transitions: door from room_lw_church_entrance; door from
  room_town_shelter; enabled placed obj_doorB from room_graveyard resolves
  room_goto_previous via scr_get_room_by_id asset order; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_lw_church_entrance; to room_town_shelter.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_krisyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_doorC`,
  `obj_doorX_musfade`, `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerD`,
  `obj_markerX`, `obj_musicer_town`, `obj_npc_sign`, `obj_overworldc`,
  `obj_sdl`, `obj_sdr`, `obj_solidblock`, `obj_town_krisyard`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_krisyard_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_ch4_LWF04A`,
  `obj_mainchara`, `obj_overworldc`, `obj_sdl`, `obj_sdr`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_mid`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_bg_palette_swap`,
  `obj_doorC`, `obj_doorD`, `obj_doorW`, `obj_doorw_musfade`, `obj_doorX`,
  `obj_lw_rain_effect`, `obj_lw_town_sideb`, `obj_mainchara`, `obj_markerC`,
  `obj_markerD`, `obj_markert`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_town`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_mid`, `obj_savepoint`, `obj_solidblock`, `obj_town_event`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_noellehouse`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_ch4_PDC08`, `obj_ch4_PDC14B`,
  `obj_doorAny`, `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerAny`,
  `obj_overworldc`, `obj_solidblockLight`, `obj_sur`.
- Incoming transitions: door from room_lw_noellehouse_main; door from
  room_town_north; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_lw_noellehouse_main; to room_town_north.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_north`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_ch4_PDC07`,
  `obj_ch4_PDC15`, `obj_doorA`, `obj_doorAny`, `obj_doorC`, `obj_doorD`,
  `obj_doorX`, `obj_flowerking`, `obj_lw_rain_dryzone`, `obj_lw_rain_effect`,
  `obj_lw_town_sideb`, `obj_mainchara`, `obj_markerAny`, `obj_markerB`,
  `obj_markerC`, `obj_markerD`, `obj_markerX`, `obj_musicer_town`,
  `obj_noellehouse_fence`, `obj_npc_room`, `obj_npc_sign`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`,
  `obj_town_north`.
- Incoming transitions: door from room_town_noellehouse; enabled placed
  obj_doorB from room_beach resolves room_goto_previous via scr_get_room_by_id
  asset order; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_town_noellehouse.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_northwest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_school`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_doorAny`, `obj_doorB`,
  `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerA`, `obj_markerX`,
  `obj_musicer_town`, `obj_overworldc`, `obj_sdr`, `obj_solidblock`,
  `obj_town_school`.
- Incoming transitions: door from room_schoollobby; enabled placed obj_doorA
  from room_town_south resolves room_goto_next via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_schoollobby.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_shelter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_doorAny`,
  `obj_doorD_musfade`, `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_room_town_shelter`, `obj_sdl`,
  `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`, `obj_town_shelter_event`.
- Incoming transitions: door from room_town_church.
- Outgoing transitions: to room_town_church.
- Conditions: No additional condition verified.

### Chapter 4: `room_town_south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_bg_palette_swap`,
  `obj_doorA`, `obj_doorC`, `obj_doorD`, `obj_doorW`, `obj_doorX`,
  `obj_lw_rain_effect`, `obj_mainchara`, `obj_markerB`, `obj_markerC`,
  `obj_markerD`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_town`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_south`, `obj_solidblock`, `obj_sul`, `obj_town_event`.
- Incoming transitions: door from room_lw_police; enabled placed obj_doorB from
  room_town_school resolves room_goto_previous via scr_get_room_by_id asset
  order; runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_townhall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_sdl`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_traintest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_homealone_heart`, `obj_mainchara`,
  `obj_overworldc`, `obj_solidblockDark`, `obj_train_controller`,
  `obj_train_station`, `obj_train_switch`, `obj_traintrack_corner_bottomleft`,
  `obj_traintrack_corner_bottomright`, `obj_traintrack_corner_topright`,
  `obj_traintrack_goal`, `obj_traintrack_moving_center`,
  `obj_traintrack_straight_horizontal`, `obj_traintrack_straight_vertical`,
  `obj_traintrack_switch`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_traintest_big`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_homealone_heart`, `obj_mainchara`,
  `obj_overworldc`, `obj_solidblockDark`, `obj_train_basket`,
  `obj_train_controller`, `obj_train_icee`, `obj_train_santa`,
  `obj_train_snowball`, `obj_train_station`, `obj_train_switch`,
  `obj_traintrack_corner_bottomleft`, `obj_traintrack_corner_bottomright`,
  `obj_traintrack_corner_topleft`, `obj_traintrack_corner_topright`,
  `obj_traintrack_fourway`, `obj_traintrack_goal`, `obj_traintrack_moving_bend`,
  `obj_traintrack_moving_center`, `obj_traintrack_ramp`, `obj_traintrack_stop`,
  `obj_traintrack_straight_horizontal`, `obj_traintrack_straight_vertical`,
  `obj_traintrack_switch`, `obj_traintrack_switch_yellow`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 4: `room_vfx_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_vfx_test`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

## Chapter 5 (252 assets)

### Chapter 5: `PLACE_CONTACT`

- Area: Player flow.
- Runtime role/status: retained contact sequence; no normal Chapter 5 dispatch
  verified; uncertain-no-ingress.
- Important controllers: `DEVICE_CONTACT_old`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `PLACE_DOG`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `PROCESS_DOG`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `PLACE_DOGCHECK_CH5`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_dogcheck_ch5`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `PLACE_DOGCHECK2`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_dogcheck2`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `PLACE_FAILURE`

- Area: Player flow.
- Runtime role/status: failure/game-over runtime destination; verified
  production reachable.
- Important controllers: `DEVICE_FAILURE`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `PLACE_LOGO`

- Area: Player flow.
- Runtime role/status: logo transition destination; verified production
  reachable.
- Important controllers: `PROCESS_LOGO`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `PLACE_MENU`

- Area: Player flow.
- Runtime role/status: title/menu runtime destination; verified production
  reachable.
- Important controllers: `DEVICE_MENU`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch;
  runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `PLACE_NAMING_JIKKEN`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `DEVICE_NAMER`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `room_alphysalley`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorW`, `obj_mainchara`, `obj_markerw`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_alphysclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_alphysdesk`, `obj_classscene`, `obj_mainchara`,
  `obj_markerA`, `obj_overworldc`, `obj_room_alphysclass`, `obj_schooldesk`,
  `obj_solidblock`, `obj_tem_school`.
- Incoming transitions: returning Light World room-specific controller/overworld
  staging with ordered room route ordered route context.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_animexampletest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_cuttableflower_example`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_animtest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_mainchara`, `obj_overworldc`,
  `obj_solidblockDark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_battletest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_battletester`, `obj_chaseenemy`,
  `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch; debug/test runtime
  dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `room_beach`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_npc_room`, `obj_npc_sign`, `obj_overworldc`, `obj_room_beach`,
  `obj_solidblock`, `obj_wave_fx`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_bullettest`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_bullettester`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `room_bullettest_new`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_bullettester_new`, `obj_darkcontroller`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_castle_tutorial`

- Area: Earlier chapter asset.
- Runtime role/status: retained earlier castle tutorial asset; no Chapter 5
  route ingress verified; uncertain-no-ingress.
- Important controllers: `obj_castle_tutorial`, `obj_darkcontroller`,
  `obj_doorW`, `obj_doorX`, `obj_mainchara`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_darkcastle`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_cc_clover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_doorD_musfade`,
  `obj_mainchara`, `obj_markerC`, `obj_npc_room`, `obj_npc_room_animated`,
  `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_cc_fountain`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_ch5_DW50`, `obj_darkfountain`.
- Incoming transitions: door from room_dw_flowery_tree.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_cc_lancer`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bluhpainting`, `obj_darkcontroller`, `obj_doorW`,
  `obj_mainchara`, `obj_markerX`, `obj_npc_room`, `obj_readable_room1`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_chapter_continue`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_chapter_continue`.
- Incoming transitions: runtime controller explicitly checks
  room_chapter_continue.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_climbtest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_climb_climbable`, `obj_climbloc`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_ramarker`, `obj_sumarker`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_cutscene_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_cutscene_test`, `obj_darkcontroller`,
  `obj_forcefield`, `obj_heightfloor`, `obj_heightfloor_changer`,
  `obj_mainchara`, `obj_npc_sign`, `obj_solidblocksized`, `obj_soliddark`,
  `obj_sticky_example`, `obj_swordobj_example`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_cutscene_tester_b`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_example_cutscene_b`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_DARKbase_GMS2`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 5: `room_darkbulbTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_shapepuzzle`, `obj_shapepuzzlebutton`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_DARKempty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 5: `room_debug_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_battle`, `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_debug_battleBalloon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_ballooner`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_debug_choicer_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_choicer`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_debug_choicer_light`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_choicer`, `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_debug_color`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_swatchling`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_debug_loc`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_loc`, `obj_hallway_mirror`, `obj_mainchara`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_solidlong`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_debug_smallface`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_smallfacetester`, `obj_mainchara`,
  `obj_overworldc`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_debug_smallface_dark`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_debug_smallfacetester`,
  `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_diner`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_catti`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_sur`, `obj_town_diner`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dogplatforming`

- Area: Flower Castle.
- Runtime role/status: optional dog platforming challenge and treasure room;
  verified production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_doorAnyHorz`, `obj_dw_dogplatforming`, `obj_genmarker`, `obj_krmarker`,
  `obj_leafpetals`, `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`,
  `obj_musicer_room`, `obj_parallax_pillars`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_checkpoint`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_plat_pinatabell`, `obj_plat_vinehook_small`, `obj_platswap`,
  `obj_platswap_statue`, `obj_ramarker`, `obj_slashpusher`,
  `obj_slashpusher_anchor`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: room_dw_fcastle_bromides door: entrance 3, music fade,
  platform mode disabled; room_dw_fcastle_top_challenge door: entrance 2.
- Outgoing transitions: to room_dw_fcastle_bromides entrance 3; to
  room_dw_fcastle_top_challenge entrance 2.
- Conditions: obj\_treasure\_room uses flag 1866, item type "item", item ID 33;
  flag 1866 marks collection.

### Chapter 5: `room_dw_castle_area_1`

- Area: Castle Town.
- Runtime role/status: Castle Town hub approach; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_dw_leave`,
  `obj_mainchara`, `obj_markerB`, `obj_markerX`, `obj_room_castle_area_1`,
  `obj_sdl_dark`, `obj_sdr_dark`, `obj_soliddark`, `obj_sul_dark`,
  `obj_sur_dark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_cafe`

- Area: Castle Town.
- Runtime role/status: Castle Town cafe; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_gen`, `obj_npc_cafe`, `obj_npc_castle_cafe`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: to room_dw_castle_town.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_church_climb`

- Area: Castle Town.
- Runtime role/status: Castle Town church climb; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climb_landingstrip`, `obj_climb_waterbucket`, `obj_climb_watergenerator`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_castle_church_climb`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_castle_church_entrance.
- Outgoing transitions: to room_dw_castle_church_entrance.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_church_entrance`

- Area: Castle Town.
- Runtime role/status: Castle Town church entrance; verified production
  reachable.
- Important controllers: `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_castle_church_entrance`, `obj_dw_church_organ`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_windowglow`.
- Incoming transitions: door from room_dw_castle_church_climb; door from
  room_dw_castle_town.
- Outgoing transitions: to room_dw_castle_church_climb; to room_dw_castle_town.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_dojo`

- Area: Castle Town.
- Runtime role/status: Castle Town dojo; verified production reachable.
- Important controllers: `obj_ch2_dojo_allstarsPlaylist`, `obj_darkcontroller`,
  `obj_dojofx`, `obj_doorAny`, `obj_mainchara`, `obj_markerX`,
  `obj_musicer_gen`, `obj_readable_room1`, `obj_room_castle_dojo`,
  `obj_solidblocksized`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: to room_dw_castle_town.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_dungeon`

- Area: Castle Town.
- Runtime role/status: Castle Town dungeon; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_king`, `obj_room_dungeon_2f`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_east_door`

- Area: Castle Town.
- Runtime role/status: Castle Town east connection; verified production
  reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_npc_castle_door`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_music`

- Area: Castle Town.
- Runtime role/status: Castle Town music room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_castle_music`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_town.
- Outgoing transitions: to room_dw_castle_town.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_restaurant`

- Area: Castle Town.
- Runtime role/status: Castle Town restaurant; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerX`, `obj_musicer_gen`, `obj_npc_castle_bakery`, `obj_sdl`,
  `obj_sdr`, `obj_soliddark`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: to room_dw_castle_town.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_rooms_kris`

- Area: Castle Town.
- Runtime role/status: Castle Town residential room for Kris; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerv`, `obj_room_castle_kris`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_rooms_ralsei`

- Area: Castle Town.
- Runtime role/status: Castle Town residential room for Ralsei; verified
  production reachable.
- Important controllers: `obj_climb_climbable`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_ramarker`, `obj_readable_room1`,
  `obj_room_castle_ralsei`, `obj_solidblockDark`, `obj_sumarker`.
- Incoming transitions: door from room_dw_ralsei_castle_3f.
- Outgoing transitions: to room_dw_ralsei_castle_3f.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_rooms_susie`

- Area: Castle Town.
- Runtime role/status: Castle Town residential room for Susie; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_musicer_darkcastle`, `obj_room_castle_susie`,
  `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_town`

- Area: Castle Town.
- Runtime role/status: Castle Town hub; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_castle_cafe`,
  `obj_castle_church`, `obj_castle_dojo`, `obj_castle_music`,
  `obj_castle_restaurant`, `obj_castle_shop`, `obj_castle_torch`,
  `obj_castle_tv`, `obj_ch5_dw_castle_town`, `obj_darkcontroller`, `obj_doorA`,
  `obj_doorAny`, `obj_doorX`, `obj_mainchara`, `obj_markerAny`, `obj_markerB`,
  `obj_markerr`, `obj_markerw`, `obj_markerX`, `obj_musicer_darkcastle`,
  `obj_room_castle_town`, `obj_savepoint`, `obj_sdl_dark`, `obj_sdr_dark`,
  `obj_solidblockDark`, `obj_sul`, `obj_sul_dark`, `obj_sur_dark`.
- Incoming transitions: door from room_dw_castle_cafe; door from
  room_dw_castle_church_entrance; door from room_dw_castle_dojo; door from
  room_dw_castle_music; door from room_dw_castle_restaurant; door from
  room_dw_castle_tv; enabled placed obj_doorA from room_town_south resolves
  room_goto_next via scr_get_room_by_id asset order; runtime dispatch; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_castle_cafe; to
  room_dw_castle_church_entrance; to room_dw_castle_dojo; to
  room_dw_castle_music; to room_dw_castle_restaurant; to room_dw_castle_tv; to
  room_shop1.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_tv`

- Area: Castle Town.
- Runtime role/status: Castle Town TV subsystem hub; verified production
  reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_ranking_hub_floor`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_darkcastle`, `obj_room_castle_tv`,
  `obj_savepoint`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_castle_town; door from
  room_dw_castle_tv_mike; door from room_dw_castle_tv_rhythm; enabled placed
  obj_doorA from room_dw_castle_town resolves room_goto_next via
  scr_get_room_by_id asset order; runtime dispatch.
- Outgoing transitions: to room_dw_castle_town; to room_dw_castle_tv_mike; to
  room_dw_castle_tv_rhythm.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_tv_kikky`

- Area: Castle Town.
- Runtime role/status: Castle Town TV subsystem: Kikky segment; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tv_zone_kikky_floor`,
  `obj_dw_tv_zone_overlay`, `obj_kikky`, `obj_kikky_screen`, `obj_mainchara`,
  `obj_markerAny`, `obj_room_castle_tv_kikky`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_tv_mike.
- Outgoing transitions: to room_dw_castle_tv_mike.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_tv_mike`

- Area: Castle Town.
- Runtime role/status: Castle Town TV subsystem: Mike segment; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_green_room_wall_fx`, `obj_dw_tv_zone_mike_floor`,
  `obj_dw_tv_zone_overlay`, `obj_mainchara`, `obj_markerAny`,
  `obj_room_castle_tv_mike`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_tv; door from
  room_dw_castle_tv_kikky; runtime dispatch.
- Outgoing transitions: to room_dw_castle_tv; to room_dw_castle_tv_kikky.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_tv_rhythm`

- Area: Castle Town.
- Runtime role/status: Castle Town TV subsystem: rhythm segment; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_blue_starry_wall`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_darkcastle`, `obj_room_castle_tv_rhythm`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_castle_tv; runtime dispatch; runtime
  dispatch.
- Outgoing transitions: to room_dw_castle_tv.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_castle_west_cliff`

- Area: Castle Town.
- Runtime role/status: Castle Town west-cliff route; conditional.
- Important controllers: `obj_darkcontroller`, `obj_doorX`, `obj_mainchara`,
  `obj_markerD`, `obj_markerX`, `obj_npc_castle_cliff`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: checks flags 468, 142, and 571 to select or suppress the room
  treasure.

### Chapter 5: `room_dw_cliff_bonuscombat`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_dw_cliff_bonuscombat`, `obj_enemy_wave`, `obj_genmarker`,
  `obj_mainchara`, `obj_markerAny40px`, `obj_parallax_cliffs`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_combatstarter`, `obj_plat_enm_bigtome`, `obj_plat_enm_book_simple`,
  `obj_plat_floor`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_pinatabell_pink`, `obj_plat_umbrellaplatform`, `obj_platswap`,
  `obj_platswap_statue`, `obj_semisolid_platform`.
- Incoming transitions: door from room_dw_cliff_twirlflowerwind; door from
  room_dw_cliff_twirlflowerwind.
- Outgoing transitions: to room_dw_cliff_twirlflowerwind; to
  room_dw_cliff_twirlflowerwind.
- Conditions: appear\_condition = global.plot >= 400 &&
  scr\_flag\_get\_ext(1731, 18) == 1;; appear\_condition = global.plot >= 400 &&
  scr\_flag\_get\_ext(1731, 18) == 1;; appear\_condition = global.plot >= 400 &&
  scr\_flag\_get\_ext(1731, 18) == 1;; appear\_condition = global.plot >= 400 &&
  scr\_flag\_get\_ext(1731, 18) == 1;.

### Chapter 5: `room_dw_cliff_bunnyfarm`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_climb_bouldergenerator`,
  `obj_climb_camera_nudger`, `obj_climb_climbable`, `obj_climb_door`,
  `obj_climb_marker`, `obj_climb_peachcatcher`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_darkslide_new`,
  `obj_doorAny`, `obj_dw_cliff_bunnyfarm`, `obj_dw_cliff_bunnyfarm_bunny`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_parallax_cliffs`,
  `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`, `obj_sunshadows`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_precipice; door from
  room_dw_cliff_precipice; door from room_dw_cliff_silver_hammer.
- Outgoing transitions: to room_dw_cliff_precipice; to room_dw_cliff_precipice;
  to room_dw_cliff_silver_hammer.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_climbrefresher`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cliff_crater`, `obj_climb_climbable`,
  `obj_climb_susie_controller`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_cliff_climbrefresher`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_cliffs`, `obj_plat_deco_bell`, `obj_plat_deco_charm`,
  `obj_ramarker`, `obj_shortcut_door`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_solidenemy_2`, `obj_sumarker`, `obj_sunshadows`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_cutdown_tutorial; door from
  room_dw_cliff_gardentransition_new.
- Outgoing transitions: to room_dw_cliff_cutdown_tutorial; to
  room_dw_cliff_gardentransition_new.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_cutdown_tutorial`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_cliff_petalwarp`, `obj_cliffglow`,
  `obj_darkcontroller`, `obj_dw_cliff_cutdown_tutorial`, `obj_enemy_wave`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_papergrass`, `obj_parallax_cliffs`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_clampzone`, `obj_plat_cam_nudgezone`,
  `obj_plat_combatstarter`, `obj_plat_enm_bigtome`, `obj_plat_enm_book_simple`,
  `obj_plat_floor`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_pinatabell_pink`, `obj_plat_sequence_marker`,
  `obj_plat_text_at_bottom_zone`, `obj_plat_vinehook`, `obj_platswap`,
  `obj_platswap_statue`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_climbrefresher; door from
  room_dw_cliff_precipice.
- Outgoing transitions: to room_dw_cliff_climbrefresher; to
  room_dw_cliff_precipice.
- Conditions: appear\_condition = global.plot < 400;; appear\_condition =
  global.plot >= 400;; appear\_condition = global.plot < 400;; appear\_condition
  = global.plot >= 400;; appear\_condition = global.plot >= 400;.

### Chapter 5: `room_dw_cliff_dash_runner`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_doorAnyVert`, `obj_dw_cliff_dash_runner`, `obj_mainchara`,
  `obj_markerAny40px`, `obj_musicer_room`, `obj_parallax_cliffs`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_checkpoint`,
  `obj_plat_coin`, `obj_plat_floor`, `obj_plat_floortex_FLOOR_AlignBottom`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_plat_wardrobe`, `obj_platswap`, `obj_platswap_statue`,
  `obj_solidblocksized_alt`, `obj_sunshadows`, `obj_torigate_dash`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_twirlflowerplatforming.
- Outgoing transitions: to room_dw_cliff_seth_miniboss; to
  room_dw_cliff_twirlflowerplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_eastcliff`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_dw_cliff_eastcliff`, `obj_genmarker`, `obj_mainchara`,
  `obj_markerAny40px`, `obj_papergrass`, `obj_parallax_cliffs`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_coin`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_pinatabell_pink`, `obj_plat_umbrellaplatform`,
  `obj_plat_windcontroller_new`, `obj_platswap`, `obj_platswap_statue`.
- Incoming transitions: door from room_dw_cliff_shicave; door from
  room_dw_cliff_verticalwind.
- Outgoing transitions: to room_dw_cliff_shicave; to room_dw_cliff_verticalwind.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_finaldash`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_doorAnyHorz`, `obj_doorAnyVert`, `obj_dw_cliff_finaldash`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`,
  `obj_papergrass`, `obj_parallax_cliffs`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_clampzone`, `obj_plat_checkpoint`,
  `obj_plat_coin`, `obj_plat_floor`, `obj_plat_floortex_BACK`,
  `obj_plat_floortex_FLOOR`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yorigin`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_platswap`, `obj_platswap_statue`, `obj_solidblocksized`,
  `obj_torigate_dash`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_netskieclimb; door from
  room_dw_cliff_shicave; door from room_dw_cliff_verticalwind.
- Outgoing transitions: to room_dw_cliff_netskieclimb; to room_dw_cliff_shicave;
  to room_dw_cliff_shicave; to room_dw_cliff_shicave; to room_dw_cliff_shicave;
  to room_dw_cliff_verticalwind.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_gardentransition_new`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_climbable`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_dash_ramp`, `obj_doorAny`, `obj_dropshadowcut`,
  `obj_dw_cliff_gardentransition_new`, `obj_dynamicshadowmask`,
  `obj_dynamicshadowmask_slope`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_cliffs`,
  `obj_solidblocksized`, `obj_sunshadows`, `obj_torigate_dash`.
- Incoming transitions: door from room_dw_cliff_climbrefresher; door from
  room_dw_garden_cliffexit.
- Outgoing transitions: to room_dw_cliff_climbrefresher; to
  room_dw_garden_cliffexit.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_kawkawdash`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bulletarea`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dropshadowcut`, `obj_dw_cliff_kawkawdash`, `obj_genmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_overworld_dashbullet_spawner`, `obj_parallax_cliffs`,
  `obj_plat_loopboundary`, `obj_solidblocksized`, `obj_sunshadows`,
  `obj_torigate_dash`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_shop; door from
  room_dw_cliff_twirlflowerwind.
- Outgoing transitions: to room_dw_cliff_shop; to room_dw_cliff_twirlflowerwind.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_netskieclimb`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_cliff_crater`,
  `obj_climb_camera_nudger`, `obj_climb_climbable`, `obj_climb_vinecuttable`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_cliff_netskieclimb`, `obj_genmarker`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_cliffs`, `obj_ramarker`,
  `obj_shortcut_door`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_solidenemy`, `obj_solidenemy_2`, `obj_sumarker`, `obj_treasure_fox`,
  `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_finaldash; door from
  room_dw_cliff_netskieclimb_behind; door from room_dw_cliff_twirlflowerwind.
- Outgoing transitions: to room_dw_cliff_finaldash; to
  room_dw_cliff_netskieclimb_behind; to room_dw_cliff_twirlflowerwind.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_netskieclimb_behind`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_cliff_netskieclimb_behind`, `obj_mainchara`, `obj_markerAny`,
  `obj_parallax_cliffs`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_cliff_netskieclimb.
- Outgoing transitions: to room_dw_cliff_netskieclimb.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_precipice`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cliff_crater`, `obj_climb_camera_nudger`,
  `obj_climb_climbable`, `obj_climb_coin`, `obj_climb_door`,
  `obj_climb_landingstrip`, `obj_climb_marker`, `obj_climb_watergenerator`,
  `obj_darkcontroller`, `obj_darkslide_new`, `obj_doorAny`, `obj_dropshadowcut`,
  `obj_dw_cliff_precipice`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_room`, `obj_overworld_scarecrow`, `obj_parallax_cliffs`,
  `obj_solidblocksized`, `obj_sunshadows`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_bunnyfarm; door from
  room_dw_cliff_bunnyfarm; door from room_dw_cliff_cutdown_tutorial; door from
  room_dw_cliff_twirlflowerplatforming.
- Outgoing transitions: to room_dw_cliff_bunnyfarm; to room_dw_cliff_bunnyfarm;
  to room_dw_cliff_cutdown_tutorial; to room_dw_cliff_twirlflowerplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_seth_miniboss`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_cliff_seth_miniboss`, `obj_genmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerAny40px`, `obj_parallax_cliffs`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_floor`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_text_at_bottom_zone`, `obj_platswap`,
  `obj_platswap_statue`, `obj_shortcut_door`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_sunshadows`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_dash_runner; door from
  room_dw_cliff_shop; door from room_dw_dogballoon; door from room_man.
- Outgoing transitions: to room_dw_cliff_shop.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_sethaqua_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_cliff_sethaqua_battle`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_cliffs`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_pinatabell`,
  `obj_platswap`, `obj_platswap_statue`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_verticalwind_post; door from
  room_dw_fcastle_entrance.
- Outgoing transitions: to room_dw_cliff_verticalwind_post; to
  room_dw_fcastle_entrance.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_shicave`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cliff_petalwarp`, `obj_darkcontroller`,
  `obj_doorAnyHorz`, `obj_dw_cliff_shicave`, `obj_mainchara`, `obj_markerAny`,
  `obj_markerAny40px`, `obj_parallax_cliffs`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_platswap`,
  `obj_platswap_statue`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_eastcliff; door from
  room_dw_cliff_finaldash; door from room_dw_cliff_finaldash; door from
  room_dw_cliff_finaldash; door from room_dw_cliff_finaldash.
- Outgoing transitions: to room_dw_cliff_eastcliff; to room_dw_cliff_finaldash.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_shop`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_cliff_shop`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_cliffs`, `obj_plat_deco_bell`, `obj_plat_deco_charm`,
  `obj_savepoint`, `obj_solidblocksized`, `obj_sunshadows`.
- Incoming transitions: door from room_dw_cliff_kawkawdash; door from
  room_dw_cliff_seth_miniboss.
- Outgoing transitions: to room_dw_cliff_kawkawdash; to
  room_dw_cliff_seth_miniboss; to room_shop_ch5.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_silver_hammer`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_cliff_silver_hammer`, `obj_mainchara`, `obj_markerAny`,
  `obj_parallax_cliffs`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_cliff_bunnyfarm.
- Outgoing transitions: to room_dw_cliff_bunnyfarm.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_twirlflowerplatforming`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_doorAnyHorz`, `obj_dropshadowcut`,
  `obj_dw_cliff_twirlflowerplatforming`, `obj_falling_leaf_area`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`, `obj_musicer_room`,
  `obj_parallax_cliffs`, `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_checkpoint`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_plat_pinatabell`, `obj_plat_slope`, `obj_plat_text_at_bottom_zone`,
  `obj_plat_twirlflower`, `obj_platswap`, `obj_platswap_statue`,
  `obj_solidblocksized`, `obj_sunshadows`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_dash_runner; door from
  room_dw_cliff_precipice; door from room_dw_cliff_yellowcave.
- Outgoing transitions: to room_dw_cliff_dash_runner; to
  room_dw_cliff_precipice; to room_dw_cliff_yellowcave.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_twirlflowerwind`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_cliff_petalwarp`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_doorAnyHorz`, `obj_dropshadowcut`,
  `obj_dw_cliff_twirlflowerwind`, `obj_falling_leaf_area`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerAny40px`, `obj_parallax_cliffs`,
  `obj_pinwheel_windspeed`, `obj_plat_action_blocker`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_checkpoint`, `obj_plat_enm_aqua_miniboss`,
  `obj_plat_floor`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_loopboundary`, `obj_plat_movemarker`, `obj_plat_pinatabell`,
  `obj_plat_sinerbullet`, `obj_plat_twirlflower`, `obj_plat_vinehook`,
  `obj_platswap`, `obj_platswap_statue`, `obj_semisolid_platform`,
  `obj_solidblocksized`, `obj_sunshadows`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_bonuscombat; door from
  room_dw_cliff_bonuscombat; door from room_dw_cliff_kawkawdash; door from
  room_dw_cliff_netskieclimb.
- Outgoing transitions: to room_dw_cliff_bonuscombat; to
  room_dw_cliff_bonuscombat; to room_dw_cliff_kawkawdash; to
  room_dw_cliff_netskieclimb.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_verticalwind`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_doorAnyVert`, `obj_dw_cliff_verticalwind`, `obj_knifewall_generator`,
  `obj_mainchara`, `obj_markerAny40px`, `obj_musicer_room`,
  `obj_parallax_cliffs`, `obj_pinwheel_windspeed`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_nudgezone`, `obj_plat_floortex_FLOOR`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_text_at_bottom_zone`, `obj_platswap`, `obj_platswap_statue`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_eastcliff; door from
  room_dw_cliff_finaldash.
- Outgoing transitions: to room_dw_cliff_eastcliff; to room_dw_cliff_finaldash;
  to room_dw_cliff_verticalwind_post.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_verticalwind_post`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dropshadowcut`, `obj_dw_cliff_verticalwind_post`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`, `obj_musicer_room`,
  `obj_parallax_cliffs`, `obj_ramarker`, `obj_savepoint`, `obj_solidblocksized`,
  `obj_sumarker`, `obj_sunshadows`.
- Incoming transitions: door from room_dw_cliff_sethaqua_battle; door from
  room_dw_cliff_verticalwind.
- Outgoing transitions: to room_dw_cliff_sethaqua_battle.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_cliff_yellowcave`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_cliff_yellowcave`, `obj_grassanim_new`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_twirlflowerplatforming.
- Outgoing transitions: to room_dw_cliff_twirlflowerplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_dogballoon`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dog_balloon`, `obj_doorAny`,
  `obj_dw_dogballoon`, `obj_grassanim_new`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_waterable_grass`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_cliff_seth_miniboss; to room_man.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_asgore`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_nudger`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_dw_fcastle_asgore`,
  `obj_dw_fcastle_top_intro`, `obj_krmarker`, `obj_mainchara`, `obj_ramarker`,
  `obj_sumarker`, `obj_trigger`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_top_intro.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_blueroom`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_ch5_DWCL02`,
  `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_fcastle_blueroom`, `obj_genmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_sdl_dark`, `obj_shortcut_door`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_dangerous_platforming.
- Outgoing transitions: to room_dw_fcastle_dangerous_platforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_bounce_1`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_bounce_1`,
  `obj_genmarker`, `obj_krmarker`, `obj_leafpetals`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_cam_nudgezone`, `obj_plat_conspiracy_new`,
  `obj_plat_conspiracywall`, `obj_plat_enm_gun`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_pinatabell`,
  `obj_plat_rosebush`, `obj_plat_text_at_bottom_zone`, `obj_platswap`,
  `obj_platswap_statue`, `obj_slashpusher`, `obj_slashpusher_anchor`,
  `obj_solidblocksized`, `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_left_twodoors; door from
  room_dw_fcastle_left_wing_floweryscene; runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_left_twodoors; to
  room_dw_fcastle_left_wing_floweryscene.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_bounce_3`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; conditional.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_dw_fcastle_bounce_3`, `obj_leafpetals`, `obj_mainchara`,
  `obj_markerAny40px`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_coin`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_pinatabell_pink`,
  `obj_platswap`, `obj_platswap_statue`, `obj_slashpush_minigame`,
  `obj_slashpusher`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_dangerous_platforming.
- Outgoing transitions: to room_dw_fcastle_dangerous_platforming.
- Conditions: appear\_condition = global.flag\[1454\] == 100;; appear\_condition
  = global.flag\[1454\] == 100;; appear\_condition = global.flag\[1454\] ==
  100;; appear\_condition = global.flag\[1454\] == 100;; appear\_condition =
  global.flag\[1454\] == 100 && scr\_flag\_get\_ext(1310, 1) == 1;.

### Chapter 5: `room_dw_fcastle_bromides`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_bromides`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_spotlight_blocker`.
- Incoming transitions: door from room_dogplatforming.
- Outgoing transitions: to room_dogplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_cafe`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_cafe`, `obj_genmarker`, `obj_leafpetals`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_savepoint`, `obj_solidblocksized`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_foyer; door from
  room_dw_fcastle_second_diner; door from room_dw_fcastle_terracotta_encounter.
- Outgoing transitions: to room_dw_fcastle_foyer; to
  room_dw_fcastle_second_diner; to room_dw_fcastle_terracotta_encounter.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_dangerous_platforming`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; conditional.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_despawn_zone`, `obj_doorAny`, `obj_doorAnyHorz`,
  `obj_dw_fcastle_dangerous_platforming`, `obj_dw_fcastle_yellow_combat`,
  `obj_genmarker`, `obj_krmarker`, `obj_leafpetals`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerAny40px`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_bulletblue_yellowhat`, `obj_plat_cam_clampzone`,
  `obj_plat_cam_nudgezone`, `obj_plat_cam_steadyzone`, `obj_plat_coin`,
  `obj_plat_floor`, `obj_plat_floortex_BACK`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yorigin`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_rosebush`, `obj_plat_sequence_marker`,
  `obj_plat_sinerbullet`, `obj_plat_text_at_bottom_zone`, `obj_plat_wardrobe`,
  `obj_platswap`, `obj_platswap_statue`, `obj_slashpusher`,
  `obj_slashpusher_anchor`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_solidenemy_2`, `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_blueroom; door from
  room_dw_fcastle_bounce_3; door from room_dw_fcastle_sandtrap.
- Outgoing transitions: to room_dw_fcastle_blueroom; to
  room_dw_fcastle_bounce_3; to room_dw_fcastle_sandtrap.
- Conditions: appear\_condition = global.flag\[1454\] == 100 &&
  scr\_flag\_get\_ext(1310, 1) == 0;; appear\_condition = global.flag\[1454\] ==
  100 && scr\_flag\_get\_ext(1310, 1) == 0;; appear\_condition =
  global.flag\[1454\] == 100 && scr\_flag\_get\_ext(1310, 1) == 0;;
  appear\_condition = global.flag\[1454\] == 100;; appear\_condition =
  global.flag\[1454\] == 100;; appear\_condition = global.flag\[1454\] == 100;;
  appear\_condition = global.flag\[1454\] == 100;; appear\_condition =
  global.flag\[1454\] == 100;.

### Chapter 5: `room_dw_fcastle_entrance`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_ch5_DW19`,
  `obj_custom_interactable_solid_circle`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_entrance`, `obj_dw_leave_flowercastle`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_cliff_sethaqua_battle; door from
  room_dw_fcastle_foyer; door from room_dw_fcastle_terracotta_puzzle.
- Outgoing transitions: to room_dw_cliff_sethaqua_battle; to
  room_dw_fcastle_foyer; to room_dw_fcastle_terracotta_puzzle.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_final_save`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_final_save`, `obj_fcastle_light`,
  `obj_leafpetals`, `obj_mainchara`, `obj_markerAny`, `obj_parallax_pillars`,
  `obj_savepoint`, `obj_shortcut_door`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_fcastle_flowery; door from
  room_dw_fcastle_orange_gauntlet.
- Outgoing transitions: to room_dw_fcastle_flowery; to
  room_dw_fcastle_orange_gauntlet.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_flowerclimb`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_climb_boostenemy`,
  `obj_climb_climbable`, `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_cloud_controller_new`, `obj_darkcontroller`,
  `obj_dw_fcastle_flowerclimb`, `obj_flowery_towery`, `obj_mainchara`,
  `obj_plat_cam_clampzone`, `obj_rotating_tower_controller_new`,
  `obj_rotating_tower_prebake_zone`, `obj_towery_flowery`, `obj_trigger`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_flowerclimb_for_tiling`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; uncertain-no-ingress.
- Important controllers: `obj_climbstarter`, `obj_climbstartertrig`,
  `obj_darkcontroller`, `obj_mainchara`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_flowery`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_flowery`, `obj_flowery_towery`,
  `obj_mainchara`, `obj_markerAny`, `obj_parallax_pillars`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_fcastle_final_save; runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_final_save.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_flowerydash`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dw_flowerydash`,
  `obj_grassanim_new`, `obj_mainchara`, `obj_parallax_cliffs`,
  `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_plat_text_at_bottom_zone`, `obj_platswap`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_foxhunt`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_bulletarea`, `obj_camera_clamper`,
  `obj_castlereflect`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_foxhunt`, `obj_fake_silhouette`, `obj_fusuma_door_small`,
  `obj_genmarker`, `obj_magicalglass`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_room`, `obj_overworld_foxbullet`,
  `obj_plat_flippainting_manager`, `obj_plat_fusumawall`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_solidenemy_2`, `obj_spotlight_blocker`,
  `obj_treasure_room`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_foxhunt_secret; door from
  room_dw_fcastle_foxhunt_secret; door from room_dw_fcastle_foxhunt_terakota;
  door from room_dw_fcastle_obscured_bullets; door from
  room_dw_fcastle_second_diner.
- Outgoing transitions: to room_dw_fcastle_foxhunt_secret; to
  room_dw_fcastle_foxhunt_terakota; to room_dw_fcastle_obscured_bullets; to
  room_dw_fcastle_second_diner.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_foxhunt_chaos`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_camera_nudger`,
  `obj_castlereflect`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_foxhunt`, `obj_fake_silhouette`, `obj_floorswitch`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_overworld_foxbullet`, `obj_parallax_wall`, `obj_plat_fusumawall`,
  `obj_solidblocksized`, `obj_solidenemy`, `obj_solidenemy_2`,
  `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_foxhunt_terakota.
- Outgoing transitions: to room_dw_fcastle_foxhunt_terakota.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_foxhunt_secret`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_foxhunt`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_plat_fusumawall`, `obj_solidblocksized`, `obj_spotlight_blocker`.
- Incoming transitions: door from room_dw_fcastle_foxhunt.
- Outgoing transitions: to room_dw_fcastle_foxhunt; to room_dw_fcastle_foxhunt.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_foxhunt_socks`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_foxhunt`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_plat_fusumawall`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_solidenemy_2`, `obj_spotlight_blocker`, `obj_treasure_room`.
- Incoming transitions: door from room_dw_fcastle_foxhunt_terakota.
- Outgoing transitions: to room_dw_fcastle_foxhunt_terakota.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_foxhunt_terakota`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_foxhunt`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_wall`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_solidblocksized_dash`, `obj_solidblocksized_nodash`, `obj_solidenemy`,
  `obj_solidenemy_2`, `obj_spotlight_blocker`,
  `obj_terracotta_stationary_overworld`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_foxhunt; door from
  room_dw_fcastle_foxhunt_chaos; door from room_dw_fcastle_foxhunt_socks.
- Outgoing transitions: to room_dw_fcastle_foxhunt; to
  room_dw_fcastle_foxhunt_chaos; to room_dw_fcastle_foxhunt_socks.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_foyer`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`, `obj_draw_at_depth`,
  `obj_dw_fcastle_foyer`, `obj_fcastle_foyer_scissor`, `obj_genmarker`,
  `obj_krmarker`, `obj_leafpile`, `obj_magicalglass`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_garden_flower_wallpaper`,
  `obj_plat_conspiracy_new`, `obj_ramarker`, `obj_sdl_dark`, `obj_sdr`,
  `obj_shortcut_door`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_solidenemy_2`, `obj_spotlight_blocker`, `obj_sul_dark`, `obj_sumarker`,
  `obj_sur_dark`, `obj_trigger`, `obj_waterable_trigger`,
  `obj_wateringcan_pedestal_huge`.
- Incoming transitions: door from room_dw_fcastle_cafe; door from
  room_dw_fcastle_entrance; door from room_dw_fcastle_onsen; door from
  room_dw_fcastle_post_party_jail; door from room_dw_fcastle_right_endingscene;
  door from room_dw_fcastle_shinobeetle_encounter; door from
  room_dw_fcastle_top_intro.
- Outgoing transitions: to room_dw_fcastle_cafe; to room_dw_fcastle_entrance; to
  room_dw_fcastle_onsen; to room_dw_fcastle_right_endingscene; to
  room_dw_fcastle_shinobeetle_encounter; to room_dw_fcastle_top_intro.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_fusumadodge`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_bulletarea`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_fusumadodge`,
  `obj_elevator_warp`, `obj_fusuma_door_small`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_overworld_sinerbullet`,
  `obj_parallax_pillars`, `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_cam_nudgezone`, `obj_plat_cam_steadyzone`,
  `obj_plat_conspiracy_new`, `obj_plat_flippainting_manager`, `obj_plat_floor`,
  `obj_plat_floortex_BACK`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_fusumawall`,
  `obj_plat_game`, `obj_plat_sinerbullet`, `obj_platswap`,
  `obj_platswap_statue`, `obj_semisolid_platform`,
  `obj_shadowplatformController`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_right_wing_floweryscene; door
  from room_dw_fcastle_terracotta_encounter; runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_right_wing_floweryscene; to
  room_dw_fcastle_terracotta_encounter.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_gloves_tower`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`, `obj_doorAnyHorz`,
  `obj_dw_fcastle_gloves_tower`, `obj_fusuma_general_mask`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerAny40px`, `obj_orange_puppet`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_cam_nudgezone`, `obj_plat_enm_glovespawner`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yorigin`, `obj_plat_floortex_Yplat`, `obj_plat_fusumawall`,
  `obj_plat_game`, `obj_plat_lantern`, `obj_plat_orangewall`, `obj_platswap`,
  `obj_platswap_statue`, `obj_semisolid_platform`, `obj_solidblocksized`,
  `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_orange_puppet_introduction;
  door from room_dw_fcastle_second_diner; door from room_dw_fcastle_trainroom.
- Outgoing transitions: to room_dw_fcastle_orange_puppet_introduction; to
  room_dw_fcastle_second_diner; to room_dw_fcastle_trainroom.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_green_checkpoint`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_green_checkpoint`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_castle_top`,
  `obj_shortcut_door`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_fcastle_top_ascent; door from
  room_dw_fcastle_top_staircase_2.
- Outgoing transitions: to room_dw_fcastle_top_ascent; to
  room_dw_fcastle_top_staircase_2.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_green_orange_battle`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_ch5_DWCR03`, `obj_custom_interactable_solid`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_onsen_steam_zone`,
  `obj_parallax_cliffs`, `obj_solidblocksized`, `obj_spotlight_blocker`,
  `obj_watersurface`.
- Incoming transitions: door from room_dw_fcastle_right_endingscene; door from
  room_dw_fcastle_right_penultimate.
- Outgoing transitions: to room_dw_fcastle_right_endingscene; to
  room_dw_fcastle_right_penultimate.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_heldmushrooms`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_heldmushrooms`, `obj_floorspike`, `obj_floorswitch`,
  `obj_held_mushroom`, `obj_mainchara`, `obj_markerAny`, `obj_parallax_cliffs`,
  `obj_plat_windcontroller_new`, `obj_solidblocksized`, `obj_sunshadows`,
  `obj_treasure_room`.
- Incoming transitions: door from room_dw_fcastle_right_penultimate.
- Outgoing transitions: to room_dw_fcastle_right_penultimate.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_left_penultimate`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_left_penultimate`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_cliffs`,
  `obj_plat_windcontroller_new`, `obj_solidblocksized`, `obj_spotlight_blocker`,
  `obj_sunshadows`.
- Incoming transitions: door from room_dw_fcastle_left_twodoors; door from
  room_dw_fcastle_shinobeetle_3d; door from room_dw_fcastle_yellowjail.
- Outgoing transitions: to room_dw_fcastle_left_twodoors; to
  room_dw_fcastle_shinobeetle_3d; to room_dw_fcastle_yellowjail.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_left_twodoors`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_left_twodoors`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`,
  `obj_spotlight_blocker`.
- Incoming transitions: door from room_dw_fcastle_bounce_1; door from
  room_dw_fcastle_left_penultimate; door from room_dw_fcastle_sandtrap; door
  from room_dw_fcastle_yellow_miniboss.
- Outgoing transitions: to room_dw_fcastle_bounce_1; to
  room_dw_fcastle_left_penultimate; to room_dw_fcastle_sandtrap; to
  room_dw_fcastle_yellow_miniboss.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_left_wing_floweryscene`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_ch5_DWCL00`, `obj_custom_interactable_solid`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_bounce_1; door from
  room_dw_fcastle_shinobeetle_encounter.
- Outgoing transitions: to room_dw_fcastle_bounce_1; to
  room_dw_fcastle_shinobeetle_encounter.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_obscured_bullets`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_ch5_DWCR02`, `obj_darkcontroller`, `obj_doorAny`, `obj_doorAnyHorz`,
  `obj_dw_fcastle_obscured_bullets`, `obj_genmarker`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`, `obj_musicer_room`,
  `obj_orange_puppet`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_bulletred_shuriken`, `obj_plat_cam_clampzone`,
  `obj_plat_cam_nudgezone`, `obj_plat_cam_steadyzone`, `obj_plat_coin`,
  `obj_plat_flippainting_manager`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_fusumawall`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_stringed_object`,
  `obj_plat_text_at_bottom_zone`, `obj_plat_toyrope`, `obj_platswap`,
  `obj_platswap_statue`, `obj_ramarker`, `obj_shadowplatformController`,
  `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_solidblocksized_nodash`, `obj_spotlight_blocker`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_foxhunt; door from
  room_dw_fcastle_right_penultimate; door from room_dw_fcastle_sidepuzzle.
- Outgoing transitions: to room_dw_fcastle_foxhunt; to
  room_dw_fcastle_right_penultimate; to room_dw_fcastle_sidepuzzle.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_onsen`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_ch5_DWC_Onsen`, `obj_custom_interactable_solid`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_onsen`, `obj_genmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_onsen_steam_zone`, `obj_parallax_cliffs`,
  `obj_savepoint`, `obj_solidblocksized`, `obj_spotlight_blocker`.
- Incoming transitions: door from room_dw_fcastle_foyer; door from
  room_dw_fcastle_yellowjail.
- Outgoing transitions: to room_dw_fcastle_foyer; to room_dw_fcastle_yellowjail.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_orange_gauntlet`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_doorAnyHorz`,
  `obj_dw_fcastle_orange_gauntlet`, `obj_enemy_wave`, `obj_genmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`, `obj_musicer_room`,
  `obj_parallax_castle_top`, `obj_parallaxer`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_enm_greenfood_egg`,
  `obj_plat_enm_orange_miniboss`, `obj_plat_enm_seth_book`,
  `obj_plat_enm_smallglove`, `obj_plat_enm_yellow_ufohat`, `obj_plat_floor`,
  `obj_plat_floortex_BACK`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_text_at_bottom_zone`,
  `obj_plat_tileset_anim`, `obj_plat_wardrobe`, `obj_platswap`,
  `obj_platswap_statue`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_final_save; door from
  room_dw_fcastle_top_ascent.
- Outgoing transitions: to room_dw_fcastle_final_save; to
  room_dw_fcastle_top_ascent.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_orange_puppet_introduction`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`, `obj_doorAnyHorz`,
  `obj_dw_fcastle_orange_puppet_introduction`, `obj_enemy_wave`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_cam_clampzone`,
  `obj_plat_cam_nudgezone`, `obj_plat_combatstarter`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_fusumawall`, `obj_plat_game`,
  `obj_plat_lantern`, `obj_plat_movemarker`, `obj_plat_orangewall`,
  `obj_plat_text_at_bottom_zone`, `obj_platswap`, `obj_platswap_statue`,
  `obj_solidblocksized`, `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_gloves_tower; door from
  room_dw_fcastle_right_puzzle.
- Outgoing transitions: to room_dw_fcastle_gloves_tower; to
  room_dw_fcastle_right_puzzle.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_partyjail`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_ch5_DW19B`, `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_spotlight_blocker`.
- Incoming transitions: door from room_dw_fcastle_post_party_jail.
- Outgoing transitions: to room_dw_fcastle_post_party_jail.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_pinkroom`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_depthsorter`, `obj_doorAny`, `obj_dw_fcastle_pinkroom`, `obj_genmarker`,
  `obj_krmarker`, `obj_leafpetals`, `obj_mainchara`, `obj_markerAny`,
  `obj_ramarker`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_spotlight_blocker`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_pinkshop; door from
  room_dw_fcastle_top_pinkdoor; door from room_dw_pink_encounter; runtime
  dispatch.
- Outgoing transitions: to room_dw_fcastle_pinkshop; to
  room_dw_fcastle_top_pinkdoor; to room_dw_pink_encounter.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_pinkshop`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_pinkshop`, `obj_mainchara`, `obj_markerAny`,
  `obj_reflect_gradient`, `obj_solid_diagonal_dark`, `obj_solidblocksized`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_pinkroom.
- Outgoing transitions: to room_dw_fcastle_pinkroom.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_post_party_jail`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_custom_interactable_solid`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_post_party_jail`, `obj_krmarker`,
  `obj_leafpetals`, `obj_mainchara`, `obj_markerAny`, `obj_ramarker`,
  `obj_savepoint`, `obj_solidblocksized`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_partyjail; runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_foyer; to room_dw_fcastle_partyjail.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_right_endingscene`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_right_endingscene`, `obj_mainchara`,
  `obj_markerAny`, `obj_onsen_steam_zone`, `obj_parallax_cliffs`,
  `obj_savepoint`, `obj_solidblocksized`, `obj_watersurface`.
- Incoming transitions: door from room_dw_fcastle_foyer; door from
  room_dw_fcastle_green_orange_battle.
- Outgoing transitions: to room_dw_fcastle_foyer; to
  room_dw_fcastle_green_orange_battle.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_right_penultimate`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_right_penultimate`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_cliffs`,
  `obj_plat_windcontroller_new`, `obj_savepoint`, `obj_solidblocksized`,
  `obj_spotlight_blocker`, `obj_sunshadows`.
- Incoming transitions: door from room_dw_fcastle_green_orange_battle; door from
  room_dw_fcastle_heldmushrooms; door from room_dw_fcastle_obscured_bullets.
- Outgoing transitions: to room_dw_fcastle_green_orange_battle; to
  room_dw_fcastle_heldmushrooms; to room_dw_fcastle_obscured_bullets.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_right_puzzle`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_right_puzzle`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_pillars`, `obj_plat_antisoftlock_zone`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_steadyzone`, `obj_plat_coin`,
  `obj_plat_conspiracy_new`, `obj_plat_flippainting_manager`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FLOOR_AlignTop`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_fusumawall`, `obj_plat_game`,
  `obj_plat_hanging_key`, `obj_plat_pinatabell_pink`,
  `obj_plat_stringed_object`, `obj_platswap`, `obj_platswap_statue`,
  `obj_shadowplatform_interactable`, `obj_shadowplatformController`,
  `obj_shortcut_door`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_orange_puppet_introduction;
  door from room_dw_fcastle_right_wing_floweryscene; runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_orange_puppet_introduction; to
  room_dw_fcastle_right_wing_floweryscene.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_right_wing_floweryscene`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_ch5_DWCR_documents`, `obj_custom_interactable_solid`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_krmarker`, `obj_mainchara`,
  `obj_markerAny`, `obj_parallax_pillars`, `obj_plat_conspiracy_new`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_fusumadodge; door from
  room_dw_fcastle_right_puzzle.
- Outgoing transitions: to room_dw_fcastle_fusumadodge; to
  room_dw_fcastle_right_puzzle.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_sandtrap`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_lilypad`, `obj_dw_fcastle_sandtrap`, `obj_leafpetals`,
  `obj_mainchara`, `obj_markerAny`, `obj_no_footprint_zone`,
  `obj_solidblocksized`, `obj_sur`, `obj_sur_nodash`, `obj_trigger`,
  `obj_zen_sand`.
- Incoming transitions: door from room_dw_fcastle_dangerous_platforming; door
  from room_dw_fcastle_left_twodoors; door from room_dw_fcastle_zenlooker.
- Outgoing transitions: to room_dw_fcastle_dangerous_platforming; to
  room_dw_fcastle_left_twodoors; to room_dw_fcastle_zenlooker.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_second_diner`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_ch5_DWCR01`,
  `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_fcastle_second_diner`, `obj_fusuma_door_small`, `obj_genmarker`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_orange_puppet`, `obj_plat_flippainting_manager`, `obj_plat_fusumawall`,
  `obj_ramarker`, `obj_savepoint`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_spotlight_blocker`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_cafe; door from
  room_dw_fcastle_foxhunt; door from room_dw_fcastle_gloves_tower.
- Outgoing transitions: to room_dw_fcastle_cafe; to room_dw_fcastle_foxhunt; to
  room_dw_fcastle_gloves_tower.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_seth_encounter`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_seth_encounter`, `obj_mainchara`, `obj_markerAny`,
  `obj_parallax_castle_top`, `obj_parallaxer`, `obj_solid_diagonal_dark`,
  `obj_solidblocksized`, `obj_solidenemy`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_top_entrance; door from
  room_dw_fcastle_yellowblue.
- Outgoing transitions: to room_dw_fcastle_top_entrance; to
  room_dw_fcastle_yellowblue.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_shadowplatformTest`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_shadowplatform_interactable`, `obj_shadowplatformController`,
  `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_shinobeetle_3d`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_shinobeetle_3d`, `obj_genmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_parallax_cliffs`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_clampzone`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_pinatabell_pink`,
  `obj_plat_shinobeetle`, `obj_plat_windcontroller_new`, `obj_platswap`,
  `obj_platswap_statue`, `obj_slashpusher`, `obj_slashpusher_anchor`,
  `obj_solidblocksized`, `obj_sunshadows`.
- Incoming transitions: door from room_dw_fcastle_left_penultimate.
- Outgoing transitions: to room_dw_fcastle_left_penultimate.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_shinobeetle_encounter`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_custom_interactable_solid`,
  `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_fcastle_shinobeetle_encounter`, `obj_leafpetals`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_no_footprint_zone`,
  `obj_ow_shinobeetle`, `obj_solidblocksized`, `obj_spotlight_blocker`,
  `obj_treasure_room`, `obj_trigger`, `obj_zen_sand`.
- Incoming transitions: door from room_dw_fcastle_foyer; door from
  room_dw_fcastle_left_wing_floweryscene; runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_foyer; to
  room_dw_fcastle_left_wing_floweryscene.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_sidepuzzle`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAnyHorz`, `obj_dw_fcastle_sidepuzzle`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerAny40px`, `obj_plat_antisoftlock_zone`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_coin`,
  `obj_plat_flippainting_manager`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FLOOR_AlignTop`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_fusumawall`, `obj_plat_game`,
  `obj_plat_pinatabell_pink`, `obj_plat_stringed_object`, `obj_plat_toyrope`,
  `obj_platswap`, `obj_platswap_statue`, `obj_shadowplatform_interactable`,
  `obj_shadowplatformController`, `obj_solidblocksized`,
  `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_obscured_bullets.
- Outgoing transitions: to room_dw_fcastle_obscured_bullets.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_terracotta_bonus`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_terracotta_bonus`, `obj_fusuma_door_small`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_pillars`, `obj_plat_flippainting_manager`,
  `obj_plat_fusumawall`, `obj_solidblocksized`, `obj_spotlight_blocker`,
  `obj_treasure_room`.
- Incoming transitions: door from room_dw_fcastle_terracotta_encounter; door
  from room_dw_fcastle_terracotta_puzzle.
- Outgoing transitions: to room_dw_fcastle_terracotta_encounter; to
  room_dw_fcastle_terracotta_puzzle.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_terracotta_encounter`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_camera_nudger`,
  `obj_castlereflect`, `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_fcastle_terracotta_encounter`, `obj_fusuma_door_small`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_pillars`, `obj_parallaxer`, `obj_plat_conspiracy_new`,
  `obj_plat_flippainting_manager`, `obj_plat_fusumawall`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_solidblocksized_dash`,
  `obj_solidblocksized_nodash`, `obj_solidenemy`, `obj_solidenemy_2`,
  `obj_spotlight_blocker`, `obj_terracotta_stationary_overworld`.
- Incoming transitions: door from room_dw_fcastle_cafe; door from
  room_dw_fcastle_fusumadodge; door from room_dw_fcastle_terracotta_bonus.
- Outgoing transitions: to room_dw_fcastle_cafe; to room_dw_fcastle_fusumadodge;
  to room_dw_fcastle_terracotta_bonus.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_terracotta_puzzle`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_terracotta_puzzle`, `obj_floorswitch`,
  `obj_mainchara`, `obj_markerAny`, `obj_parallax_pillars`, `obj_plat_toyrope`,
  `obj_solidblocksized`, `obj_solidblocksized_alt`, `obj_solidenemy`,
  `obj_spotlight_blocker`, `obj_terracotta_stationary_overworld`,
  `obj_treasure_room`.
- Incoming transitions: door from room_dw_fcastle_entrance; door from
  room_dw_fcastle_terracotta_bonus.
- Outgoing transitions: to room_dw_fcastle_entrance; to
  room_dw_fcastle_terracotta_bonus.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_ascent`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_doorAnyHorz`, `obj_dw_fcastle_top_ascent`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`,
  `obj_musicer_room`, `obj_parallax_castle_top`, `obj_parallaxer`,
  `obj_plat_block`, `obj_plat_cam_clampzone`, `obj_plat_cam_nudgezone`,
  `obj_plat_checkpoint`, `obj_plat_coin`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_plat_pinatabell`, `obj_plat_pumpkin`, `obj_plat_sequence_marker`,
  `obj_plat_tileset_anim`, `obj_plat_vinehook_small`, `obj_plat_zipline`,
  `obj_platswap`, `obj_platswap_statue`, `obj_semisolid_platform`,
  `obj_slashpusher`, `obj_slashpusher_anchor`, `obj_solidblocksized`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_green_checkpoint; door from
  room_dw_fcastle_orange_gauntlet; door from room_dw_fcastle_top_challenge.
- Outgoing transitions: to room_dw_fcastle_green_checkpoint; to
  room_dw_fcastle_orange_gauntlet; to room_dw_fcastle_top_challenge.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_challenge`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_bramble`, `obj_camera_clamper`,
  `obj_darkcontroller`, `obj_doorAnyHorz`, `obj_doorAnyVert`,
  `obj_dw_fcastle_top_challenge`, `obj_mainchara`, `obj_markerAny40px`,
  `obj_musicer_room`, `obj_parallax_castle_top`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_cam_steadyzone`, `obj_plat_checkpoint`,
  `obj_plat_coin`, `obj_plat_floor`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_pinatabell_pink`, `obj_plat_rosebush`,
  `obj_plat_sinerbullet`, `obj_plat_text_at_bottom_zone`,
  `obj_plat_vinehook_small`, `obj_platswap`, `obj_semisolid_platform`,
  `obj_slashpusher`, `obj_slashpusher_anchor`, `obj_trigger`.
- Incoming transitions: door from room_dogplatforming; door from
  room_dw_fcastle_top_ascent; door from room_dw_fcastle_top_descent.
- Outgoing transitions: to room_dogplatforming; to room_dw_fcastle_top_ascent;
  to room_dw_fcastle_top_descent.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_descent`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyVert`,
  `obj_dw_fcastle_top_descent`, `obj_mainchara`, `obj_markerAny40px`,
  `obj_parallax_castle_top`, `obj_pinwheel_windspeed`, `obj_plat_block`,
  `obj_plat_cam_nudgezone`, `obj_plat_enm_gun`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_rosebush`,
  `obj_platswap`, `obj_platswap_statue`, `obj_slashpusher`,
  `obj_slashpusher_anchor`, `obj_windflip_platform`.
- Incoming transitions: door from room_dw_fcastle_top_challenge.
- Outgoing transitions: to room_dw_fcastle_top_challenge; to
  room_dw_fcastle_top_pinkdoor.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_entrance`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_room`, `obj_parallax_castle_top`,
  `obj_savepoint`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_fcastle_seth_encounter; door from
  room_dw_fcastle_top_intro.
- Outgoing transitions: to room_dw_fcastle_seth_encounter; to
  room_dw_fcastle_top_intro.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_fountain`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_ch5_DW45`, `obj_ch5_DW45_fountain`,
  `obj_darkcontroller`, `obj_mainchara`, `obj_markerAny`, `obj_solidblockDark`.
- Incoming transitions: door from room_dw_post_flowery_battle.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_intro`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_top_intro`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_plat_conspiracy_new`, `obj_plat_fusumawall`, `obj_ramarker`,
  `obj_solidblockDark`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_spotlight_blocker`, `obj_sumarker`.
- Incoming transitions: door from room_dw_fcastle_asgore; door from
  room_dw_fcastle_foyer; door from room_dw_fcastle_top_entrance; door from
  room_dw_fcastle_top_pinkdoor.
- Outgoing transitions: to room_dw_fcastle_foyer; to
  room_dw_fcastle_top_entrance; to room_dw_fcastle_top_pinkdoor.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_pinkdoor`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_top_pinkdoor`,
  `obj_genmarker`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_markerAny40px`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_floor`, `obj_plat_floortex_BACK`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_pinatabell_pink`,
  `obj_platswap`, `obj_platswap_statue`, `obj_ramarker`, `obj_shortcut_door`,
  `obj_solidblocksized`, `obj_solidblocksized_alt`, `obj_spotlight_blocker`,
  `obj_sumarker`.
- Incoming transitions: door from room_dw_fcastle_pinkroom; door from
  room_dw_fcastle_top_descent; door from room_dw_fcastle_top_intro.
- Outgoing transitions: to room_dw_fcastle_pinkroom; to
  room_dw_fcastle_top_intro.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_staircase_1`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_castlereflect`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_top_staircase_1`,
  `obj_fcastle_light`, `obj_leafpetals`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_room`, `obj_parallax_pillars`, `obj_reflect_gradient`,
  `obj_solid_diagonal_dark`, `obj_solidblocksized`, `obj_spotlight_blocker`,
  `obj_sul_dark`.
- Incoming transitions: door from room_dw_fcastle_ultradash; door from
  room_dw_fcastle_yellowblue.
- Outgoing transitions: to room_dw_fcastle_ultradash; to
  room_dw_fcastle_yellowblue.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_top_staircase_2`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_top_staircase_2`, `obj_fcastle_light`,
  `obj_leafpetals`, `obj_mainchara`, `obj_markerAny`, `obj_parallax_pillars`,
  `obj_reflect_gradient`, `obj_solid_diagonal_dark`, `obj_solidblocksized`,
  `obj_sul_dark`.
- Incoming transitions: door from room_dw_fcastle_green_checkpoint; door from
  room_dw_fcastle_ultradash.
- Outgoing transitions: to room_dw_fcastle_green_checkpoint; to
  room_dw_fcastle_ultradash.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_trainroom`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_dw_fcastle_trainroom`, `obj_mainchara`, `obj_markerAny40px`,
  `obj_orange_puppet`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_cam_nudgezone`, `obj_plat_enm_glovespawner`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_fusumawall`, `obj_plat_game`,
  `obj_plat_lantern`, `obj_platswap`, `obj_platswap_statue`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_gloves_tower.
- Outgoing transitions: to room_dw_fcastle_gloves_tower.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_ultradash`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_fcastle_ultradash`, `obj_floradinn_overworld`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_castle_top`, `obj_parallaxer`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_clampzone`, `obj_plat_cam_steadyzone`,
  `obj_plat_checkpoint`, `obj_plat_coin`, `obj_plat_dash_aqua`,
  `obj_plat_floor`, `obj_plat_floortex_BACK`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_loopboundary`,
  `obj_plat_movemarker`, `obj_plat_text_at_bottom_zone`,
  `obj_plat_tileset_anim`, `obj_platswap`, `obj_platswap_statue`,
  `obj_slashpusher`, `obj_slashpusher_anchor`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_solidenemy`, `obj_torigate_dash`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_top_staircase_1; door from
  room_dw_fcastle_top_staircase_2.
- Outgoing transitions: to room_dw_fcastle_top_staircase_1; to
  room_dw_fcastle_top_staircase_2.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_yellow_miniboss`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_ch5_DWCL01`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_yellow_miniboss`,
  `obj_genmarker`, `obj_leafpetals`, `obj_mainchara`, `obj_markerAny`,
  `obj_plat_block`, `obj_plat_blueflower`, `obj_plat_cam_clampzone`,
  `obj_plat_cam_nudgezone`, `obj_plat_cam_steadyzone`, `obj_plat_coin`,
  `obj_plat_enm_yellow_miniboss`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_plat_text_at_bottom_zone`, `obj_platswap`, `obj_platswap_statue`,
  `obj_slashpusher`, `obj_slashpusher_anchor`, `obj_solidblocksized`,
  `obj_spotlight_blocker`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_left_twodoors.
- Outgoing transitions: to room_dw_fcastle_left_twodoors.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_yellowblue`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; conditional.
- Important controllers: `obj_blue_platform`, `obj_camera_clamper`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_yellowblue`,
  `obj_genmarker`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`,
  `obj_parallax_castle_top`, `obj_parallaxer`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_clampzone`, `obj_plat_cam_nudgezone`,
  `obj_plat_checkpoint`, `obj_plat_coin`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yorigin`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_text_at_bottom_zone`, `obj_platswap`,
  `obj_platswap_statue`, `obj_shootable_terrain`, `obj_slashpusher`,
  `obj_slashpusher_anchor`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_solidenemy`, `obj_trigger`, `obj_yellow_background_controller`.
- Incoming transitions: door from room_dw_fcastle_seth_encounter; door from
  room_dw_fcastle_top_staircase_1.
- Outgoing transitions: to room_dw_fcastle_seth_encounter; to
  room_dw_fcastle_top_staircase_1.
- Conditions: appear\_condition = global.plot >= 460;; appear\_condition =
  global.plot >= 460;; appear\_condition = global.plot >= 460;;
  appear\_condition = global.plot >= 460;; appear\_condition = global.plot >=
  460;; appear\_condition = global.plot >= 460;; appear\_condition =
  global.plot >= 460;; appear\_condition = global.plot >= 460;;
  appear\_condition = global.plot >= 460;.

### Chapter 5: `room_dw_fcastle_yellowjail`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_ch5_DWCL03`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_fcastle_yellowjail`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`,
  `obj_spotlight_blocker`, `obj_spotlight_wall`, `obj_trigger`.
- Incoming transitions: door from room_dw_fcastle_left_penultimate; door from
  room_dw_fcastle_onsen.
- Outgoing transitions: to room_dw_fcastle_left_penultimate; to
  room_dw_fcastle_onsen.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_fcastle_zenlooker`

- Area: Flower Castle.
- Runtime role/status: Flower Castle route room; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_zenlooker`, `obj_leafpetals`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_treasure_room`, `obj_zen_sand`.
- Incoming transitions: door from room_dw_fcastle_sandtrap.
- Outgoing transitions: to room_dw_fcastle_sandtrap.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_flowery_tree`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_flowery_tree`, `obj_krmarker`, `obj_leafpetals`,
  `obj_mainchara`, `obj_markerAny`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_sumarker`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_cc_fountain.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_aqua`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_aqua`, `obj_grassanim_new`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_aquadarkness; door from
  room_dw_garden_wateringcan_aqua.
- Outgoing transitions: to room_dw_garden_aquadarkness; to
  room_dw_garden_wateringcan_aqua.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_aquadarkness`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkslide_new`,
  `obj_doorAny`, `obj_dw_garden_aquadarkness`, `obj_grassanim_new`,
  `obj_mainchara`, `obj_markerAny`, `obj_sdl_dark`, `obj_sdr_dark`,
  `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_aqua.
- Outgoing transitions: to room_dw_garden_aqua; to room_dw_garden_aquahole.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_aquadash`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch5_DW08`, `obj_climb_climbable`,
  `obj_climb_door`, `obj_climb_marker`, `obj_climbstarter`,
  `obj_climbstartertrig`, `obj_darkcontroller`, `obj_depthsorter`,
  `obj_doorAny`, `obj_dw_garden_aquadash`, `obj_dw_garden_exit`,
  `obj_dw_leave_flowery`, `obj_grassanim_new`, `obj_krmarker`, `obj_leafpetals`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_room`, `obj_plat_game`,
  `obj_plat_pinatabell_pink`, `obj_ramarker`, `obj_sdl_dark`, `obj_sdr_dark`,
  `obj_shortcut_door`, `obj_solidblocksized`, `obj_sul_dark`, `obj_sumarker`,
  `obj_sur_dark`, `obj_torigate_dash`, `obj_trigger`, `obj_waterpit`.
- Incoming transitions: door from room_dw_garden_aquaplatforming; door from
  room_dw_garden_aquatransition; door from room_dw_garden_aquatransition; door
  from room_dw_garden_finalplatforming.
- Outgoing transitions: to room_dw_garden_aquaplatforming; to
  room_dw_garden_aquatransition; to room_dw_garden_aquatransition; to
  room_dw_garden_finalplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_aquadash_plat`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; verified production reachable.
- Important controllers: `obj_ch5_DW08`, `obj_darkcontroller`,
  `obj_depthsorter`, `obj_doorAnyHorz`, `obj_dw_garden_aquadash_plat`,
  `obj_dw_garden_exit`, `obj_dw_leave_flowery`, `obj_enemy_wave`,
  `obj_genmarker`, `obj_grassanim_new`, `obj_leafpetals`, `obj_mainchara`,
  `obj_markerAny40px`, `obj_musicer_room`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_coin`, `obj_plat_combatstarter`,
  `obj_plat_enm_aqua_miniboss`, `obj_plat_enm_aqua_sword`,
  `obj_plat_floortex_FLOOR`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yorigin`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_pinatabell_pink`,
  `obj_platswap`, `obj_shortcut_door`, `obj_torigate_dash`, `obj_waterpit`.
- Incoming transitions: door from room_dw_garden_finalplatforming; door from
  room_dw_garden_finalplatforming.
- Outgoing transitions: to room_dw_garden_finalplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_aquahole`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_doorAnyHorz`, `obj_dw_garden_aquahole`,
  `obj_grassanim_new`, `obj_leafplatform`, `obj_mainchara`, `obj_markerAny`,
  `obj_markerAny40px`, `obj_musicer_bird_new`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_nudgezone`, `obj_plat_floortex_BACK`,
  `obj_plat_floortex_FLOOR`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_pinatabell`, `obj_plat_sequence_marker`,
  `obj_plat_text_at_bottom_zone`, `obj_platmode_recolor`, `obj_platswap`,
  `obj_platswap_statue`, `obj_savepoint`, `obj_solidblocksized`,
  `obj_solidenemy`.
- Incoming transitions: door from room_dw_garden_aquadarkness; door from
  room_dw_garden_aquahole_left; door from room_dw_garden_aquahole_left; door
  from room_dw_garden_aquashrine; door from room_dw_garden_aquatransition.
- Outgoing transitions: to room_dw_garden_aquahole_left; to
  room_dw_garden_aquahole_left; to room_dw_garden_aquashrine.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_aquahole_left`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; conditional.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_dw_garden_aquahole_left`, `obj_grassanim_new`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerAny40px`, `obj_musicer_bird_new`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_enm_aqua_gold`,
  `obj_plat_floortex_BACK`, `obj_plat_floortex_FLOOR`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_pinatabell`,
  `obj_platmode_recolor`, `obj_platswap`, `obj_platswap_statue`,
  `obj_shortcut_door`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_garden_aquahole; door from
  room_dw_garden_aquahole.
- Outgoing transitions: to room_dw_garden_aquahole; to room_dw_garden_aquahole.
- Conditions: appear\_condition = global.plot >= 295 && global.flag\[1896\] ==
  0;.

### Chapter 5: `room_dw_garden_aquaplatforming`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; conditional.
- Important controllers: `obj_bramble`, `obj_camera_clamper`,
  `obj_climb_climbable`, `obj_climb_door`, `obj_climb_marker`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_darkfruit_tree_plat`, `obj_doorAnyHorz`, `obj_dw_garden_aquaplatforming`,
  `obj_grassanim_new`, `obj_krmarker`, `obj_leafplatform`, `obj_mainchara`,
  `obj_markerAny40px`, `obj_musicer_bird_new`, `obj_papergrass`,
  `obj_plat_attacktrigger`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_cam_clampzone`, `obj_plat_cam_nudgezone`, `obj_plat_cam_steadyzone`,
  `obj_plat_enm_aqua_bouncer`, `obj_plat_enm_aqua_miniboss`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yorigin`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_plat_pinatabell`, `obj_plat_pinatabell_pink`,
  `obj_plat_pumpkin`, `obj_plat_sequence_marker`,
  `obj_plat_text_at_bottom_zone`, `obj_plat_vinehook_small`,
  `obj_plat_wardrobe`, `obj_platmode_recolor`, `obj_platswap`,
  `obj_platswap_statue`, `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_garden_aquadash; door from
  room_dw_garden_aquashrine.
- Outgoing transitions: to room_dw_garden_aquadash; to
  room_dw_garden_aquashrine.
- Conditions: appear\_condition = global.plot >= 295;; appear\_condition =
  global.plot >= 295;; appear\_condition = global.plot >= 295;;
  appear\_condition = global.plot >= 295;; appear\_condition = global.plot >=
  295;; appear\_condition = global.plot >= 295;; appear\_condition =
  global.plot >= 295;; appear\_condition = global.plot >= 295;;
  appear\_condition = global.plot >= 295;; appear\_condition = global.plot >=
  295;.

### Chapter 5: `room_dw_garden_aquashrine`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_dw_garden_aquashrine`, `obj_genmarker`, `obj_grassanim_new`,
  `obj_mainchara`, `obj_markerAny40px`, `obj_plat_aquashrine`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_floor`,
  `obj_plat_floortex_BACK`, `obj_plat_floortex_FLOOR`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_platformfeather`, `obj_platmode_recolor`,
  `obj_platswap`, `obj_platswap_statue`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_garden_aquahole; door from
  room_dw_garden_aquaplatforming.
- Outgoing transitions: to room_dw_garden_aquahole; to
  room_dw_garden_aquaplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_aquatransition`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_pink_bg`, `obj_camera_clamper`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_garden_aquadarkness`,
  `obj_grassanim_new`, `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_garden_aquadash; door from
  room_dw_garden_aquadash; door from room_dw_garden_diner; door from
  room_dw_garden_diner; door from room_dw_garden_hardpressureplates; door from
  room_dw_garden_wateringcan_aqua.
- Outgoing transitions: to room_dw_garden_aquadash; to room_dw_garden_aquadash;
  to room_dw_garden_aquahole; to room_dw_garden_diner; to room_dw_garden_diner;
  to room_dw_garden_hardpressureplates; to room_dw_garden_wateringcan_aqua.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_cliffexit`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_ch5_DW10`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_cliffexit`, `obj_mainchara`, `obj_markerAny`,
  `obj_parallax_cliffs`, `obj_savepoint`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_cliff_gardentransition_new; door from
  room_dw_garden_finalplatforming.
- Outgoing transitions: to room_dw_cliff_gardentransition_new; to
  room_dw_garden_finalplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_diner`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_garden_diner`, `obj_dw_garden_diner_bouncingstools`, `obj_genmarker`,
  `obj_grassanim_new`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_ramarker`, `obj_solidblocksized`, `obj_sul_dark`, `obj_sumarker`,
  `obj_sur_dark`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_aquatransition; door from
  room_dw_garden_aquatransition; door from room_dw_garden_firstdash; door from
  room_dw_garden_newdash.
- Outgoing transitions: to room_dw_garden_aquatransition; to
  room_dw_garden_aquatransition; to room_dw_garden_firstdash; to
  room_dw_garden_newdash.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_enemyrush`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_pink_bg`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_garden_enemyrush`, `obj_genmarker`,
  `obj_grassanim_new`, `obj_krmarker`, `obj_mainchara`, `obj_markerAny`,
  `obj_pinktree`, `obj_ramarker`, `obj_sakurafubuki_mini`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_trigger`,
  `obj_waterable_flower_cluster`, `obj_waterable_grass`,
  `obj_waterable_trigger`.
- Incoming transitions: door from room_dw_garden_pedestal; door from
  room_dw_garden_shearydodge; door from room_dw_garden_shearyguide.
- Outgoing transitions: to room_dw_garden_pedestal; to
  room_dw_garden_shearydodge; to room_dw_garden_shearyguide.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_finalplatforming`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_cliff_wind_animator`, `obj_climb_climbable`,
  `obj_climbstarter`, `obj_climbstartertrig`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_doorAnyHorz`, `obj_dw_garden_finalplatforming`,
  `obj_genmarker`, `obj_grassanim_new`, `obj_krmarker`, `obj_leafpetals`,
  `obj_leafplatform`, `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`,
  `obj_parallax_cliffs`, `obj_plat_autoblock`, `obj_plat_block`,
  `obj_plat_floor`, `obj_plat_floortex_BACK`, `obj_plat_floortex_FLOOR`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yorigin`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_sequence_marker`,
  `obj_plat_vinehook_small`, `obj_platmode_recolor`, `obj_platswap`,
  `obj_platswap_statue`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_aquadash; door from
  room_dw_garden_aquadash_plat; door from room_dw_garden_cliffexit; door from
  room_dw_garden_finalplatforming_right.
- Outgoing transitions: to room_dw_garden_aquadash; to
  room_dw_garden_aquadash_plat; to room_dw_garden_aquadash_plat; to
  room_dw_garden_cliffexit; to room_dw_garden_finalplatforming_right; to
  room_dw_garden_finalplatforming_right.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_finalplatforming_right`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAnyHorz`,
  `obj_dw_garden_finalplatforming_right`, `obj_grassanim_new`, `obj_leafpetals`,
  `obj_leafplatform`, `obj_mainchara`, `obj_markerAny40px`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_cam_nudgezone`,
  `obj_plat_floor`, `obj_plat_floortex_BACK`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_movemarker`,
  `obj_plat_pinatabell`, `obj_plat_testtarget`, `obj_platmode_recolor`,
  `obj_platswap`, `obj_platswap_statue`, `obj_solidblocksized`,
  `obj_solidenemy`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_finalplatforming; door from
  room_dw_garden_finalplatforming.
- Outgoing transitions: to room_dw_garden_finalplatforming.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_firstdash`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_firstdash`, `obj_grassanim_new`, `obj_leaf_treasure_chest`,
  `obj_leafpile`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`,
  `obj_parallax_garden_flower_lights`, `obj_pinktree`, `obj_rock3d`,
  `obj_sdl_dark`, `obj_sdr_dark`, `obj_solidblocksized`,
  `obj_solidblocksized_dash`, `obj_sul_dark`, `obj_sur_dark`,
  `obj_torigate_dash`, `obj_waterfallanim`, `obj_waterpit`.
- Incoming transitions: door from room_dw_garden_diner; door from
  room_dw_garden_platshortcut; door from room_dw_garden_shearyguide.
- Outgoing transitions: to room_dw_garden_diner; to room_dw_garden_platshortcut;
  to room_dw_garden_shearyguide.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_fishingspot`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_pink_bg`, `obj_camera_clamper`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_garden_fishingspot`,
  `obj_dw_garden_shearyencounter_waves`, `obj_fishingboat`, `obj_grassanim_new`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`, `obj_npc_doubter`,
  `obj_pinktree`, `obj_reedanim`, `obj_sakurafubuki_mini`,
  `obj_solidblocksized`, `obj_waterable_trigger`.
- Incoming transitions: door from room_dw_garden_floradinnencounter.
- Outgoing transitions: to room_dw_garden_floradinnencounter.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_floradinnencounter`

- Area: Area not established.
- Runtime role/status: Save-point interaction and route staging; verified
  production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_blocktree_pink_bg`,
  `obj_camera_clamper`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_floradinnencounter`, `obj_dw_garden_ribbonchest`,
  `obj_dw_garden_shearyencounter_waves`, `obj_grassanim_new`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`, `obj_pinktree`,
  `obj_plat_game`, `obj_reedanim`, `obj_sakurafubuki_new`, `obj_savepoint`,
  `obj_sdl_dark`, `obj_sdr_dark`, `obj_solidblocksized`,
  `obj_solidblocksized_alt`, `obj_solidenemy`, `obj_spinpetalmaker`,
  `obj_sul_dark`, `obj_sur_dark`, `obj_trigger`, `obj_waterable_trigger`,
  `obj_wateringcan_pedestal`, `obj_waterreflect`.
- Incoming transitions: door from room_dw_garden_fishingspot; door from
  room_dw_garden_hospital; door from room_dw_garden_mushrooms; door from
  room_dw_garden_ralseicupboard; runtime dispatch.
- Outgoing transitions: to room_dw_garden_fishingspot; to
  room_dw_garden_mushrooms; to room_dw_garden_ralseicupboard.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_flowerygardening`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_flowerygardening`, `obj_grassanim_new`,
  `obj_item_knock_off_bar`, `obj_krmarker`, `obj_layer_to_waterable_assets`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`, `obj_plat_game`,
  `obj_ramarker`, `obj_solidblocksized`, `obj_sumarker`,
  `obj_waterable_flower_cluster`, `obj_waterable_flower_small`,
  `obj_wateringcan_pedestal`.
- Incoming transitions: door from room_dw_garden_shearyguide.
- Outgoing transitions: to room_dw_garden_shearyguide.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_hardpressureplates`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_ch5_DW05`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_garden_hardpressureplates`,
  `obj_floorcolour`, `obj_floorspike`, `obj_genmarker`, `obj_glowtile_new`,
  `obj_glowtile_puzzle_new`, `obj_grassanim_new`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_garden`, `obj_parallax_garden_flower_lights`,
  `obj_plat_game`, `obj_solidblocksized`, `obj_solidblocksized_alt`,
  `obj_trigger`.
- Incoming transitions: door from room_dw_garden_aquatransition; door from
  room_dw_garden_newdash; door from room_dw_garden_susiechase.
- Outgoing transitions: to room_dw_garden_aquatransition; to
  room_dw_garden_newdash; to room_dw_garden_susiechase.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_hopschef`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_camera_nudger`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_doorAnyHorz`,
  `obj_dw_garden_hopschef`, `obj_genmarker`, `obj_grassanim_new`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerAny40px`, `obj_musicer_garden`,
  `obj_pinktree_bottomorigin`, `obj_pinktree_tall`, `obj_plat_autoblock`,
  `obj_plat_block`, `obj_plat_cam_clampzone`, `obj_plat_floor`,
  `obj_plat_floortex_BACK`, `obj_plat_floortex_FLOOR`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yorigin`, `obj_plat_floortex_Yplat`, `obj_plat_game`,
  `obj_plat_movemarker`, `obj_platswap`, `obj_platswap_statue`,
  `obj_shortcut_door`, `obj_slashpusher`, `obj_slashpusher_anchor`,
  `obj_smalldough`, `obj_solidblocksized`, `obj_trigger`,
  `obj_waterable_trigger`.
- Incoming transitions: door from room_dw_garden_platshortcut; door from
  room_dw_garden_shearydodge.
- Outgoing transitions: to room_dw_garden_platshortcut; to
  room_dw_garden_shearydodge.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_hospital`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_hospital`, `obj_grassanim_new`, `obj_mainchara`,
  `obj_markerAny`, `obj_readable_room1`, `obj_solidblocksized`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_garden_floradinnencounter.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_intro`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_ch5_LW21_arrive`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_garden_intro`, `obj_garden_glower`, `obj_glow_flower`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_garden_meetflowery; runtime dispatch.
- Outgoing transitions: to room_dw_garden_meetflowery.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_meetflowery`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_ch5_DW01`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_garden_meetflowery`,
  `obj_garden_glower`, `obj_genmarker`, `obj_glow_flower`, `obj_mainchara`,
  `obj_markerAny`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_intro; door from
  room_dw_garden_ralseicupboard; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_dw_garden_intro; to
  room_dw_garden_ralseicupboard.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_mushrooms`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_canopy_shadow`,
  `obj_darkcontroller`, `obj_depthsorter`, `obj_doorAny`,
  `obj_dw_garden_mushrooms`, `obj_floorspike`, `obj_floorswitch`,
  `obj_grassanim_new`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`,
  `obj_pushable_block`, `obj_solidblocksized`, `obj_solidenemy`,
  `obj_treasure_room_altsolid`, `obj_trigger`, `obj_waterable_trigger`.
- Incoming transitions: door from room_dw_garden_floradinnencounter; door from
  room_dw_garden_shearydodge.
- Outgoing transitions: to room_dw_garden_floradinnencounter; to
  room_dw_garden_shearydodge.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_newdash`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_darkslide_new`, `obj_doorAny`, `obj_dw_garden_newdash`, `obj_genmarker`,
  `obj_grassanim_new`, `obj_leafpile`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_garden`, `obj_parallax_garden_flower_lights`, `obj_rock3d`,
  `obj_solidblocksized`, `obj_solidblocksized_dash`,
  `obj_solidblocksized_nodash`, `obj_torigate_dash`, `obj_treasure_room`,
  `obj_trigger`, `obj_waterfallanim`, `obj_waterpit`.
- Incoming transitions: door from room_dw_garden_diner; door from
  room_dw_garden_hardpressureplates.
- Outgoing transitions: to room_dw_garden_diner; to
  room_dw_garden_hardpressureplates.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_pedestal`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_pedestal`, `obj_grassanim_new`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`, `obj_ramarker`,
  `obj_solidblocksized`, `obj_sumarker`, `obj_waterable_flower_2x2`,
  `obj_waterable_flower_cluster`, `obj_waterable_grass`,
  `obj_wateringcan_pedestal`.
- Incoming transitions: door from room_dw_garden_enemyrush.
- Outgoing transitions: to room_dw_garden_enemyrush.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_platshortcut`

- Area: Area not established.
- Runtime role/status: Boss or battle-event staging driven by its placed
  encounter controller; conditional.
- Important controllers: `obj_bramble`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_doorAnyHorz`, `obj_dw_garden_platshortcut`, `obj_enemy_wave`,
  `obj_genmarker`, `obj_grassanim_new`, `obj_leafplatform`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerAny40px`, `obj_musicer_garden`,
  `obj_parallax_garden_flower_lights`, `obj_pinktree_tall`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_combatstarter`,
  `obj_plat_enm_aqua_bouncer`, `obj_plat_enm_aqua_miniboss`, `obj_plat_floor`,
  `obj_plat_floortex_FLOOR_AlignBottom1TILE`, `obj_plat_floortex_FRONT`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_plat_vinehook_small`,
  `obj_platswap`, `obj_platswap_statue`, `obj_solidblocksized`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_firstdash; door from
  room_dw_garden_hopschef; door from room_dw_garden_starwalkerdash.
- Outgoing transitions: to room_dw_garden_firstdash; to room_dw_garden_hopschef;
  to room_dw_garden_starwalkerdash.
- Conditions: appear\_condition = global.plot >= 300 &&
  scr\_flag\_get\_ext(1300, 1);.

### Chapter 5: `room_dw_garden_ralseicupboard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_dw_garden_ralseicupboard`, `obj_garden_glower`,
  `obj_gardenlight`, `obj_genmarker`, `obj_glow_flower`, `obj_krmarker`,
  `obj_mainchara`, `obj_markerAny`, `obj_ramarker`, `obj_solidblocksized`,
  `obj_sumarker`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_floradinnencounter; door from
  room_dw_garden_meetflowery.
- Outgoing transitions: to room_dw_garden_floradinnencounter; to
  room_dw_garden_meetflowery.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_riverchest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_riverchest`, `obj_dw_garden_shearyencounter_waves`,
  `obj_grassanim_new`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`,
  `obj_pinktree`, `obj_reedanim`, `obj_solidblocksized`, `obj_spinpetalmaker`,
  `obj_treasure_room`.
- Incoming transitions: door from room_dw_garden_shearydodge.
- Outgoing transitions: to room_dw_garden_shearydodge.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_shearydodge`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bulletarea`, `obj_camera_clamper`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_garden_shearydodge`,
  `obj_grassanim_new`, `obj_lightfairy`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_garden`, `obj_pinktree`, `obj_scissor_flower_chaser_scissor`,
  `obj_solidblocksized`, `obj_treasure_room`, `obj_waterable_flower_2x2`,
  `obj_waterable_flower_cluster`, `obj_waterable_grass`,
  `obj_wateringcan_pedestal`.
- Incoming transitions: door from room_dw_garden_enemyrush; door from
  room_dw_garden_hopschef; door from room_dw_garden_mushrooms; door from
  room_dw_garden_riverchest.
- Outgoing transitions: to room_dw_garden_enemyrush; to room_dw_garden_hopschef;
  to room_dw_garden_mushrooms; to room_dw_garden_riverchest.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_shearyguide`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_pink_bg`, `obj_camera_clamper`,
  `obj_darkcontroller`, `obj_doorAny`, `obj_dw_garden_shearyguide`,
  `obj_genmarker`, `obj_grassanim_new`, `obj_item_knock_off_bar`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_pinktree`,
  `obj_plat_game`, `obj_ramarker`, `obj_scissor_flower_chaser_scissor`,
  `obj_solidblocksized`, `obj_solidblocksized_alt`, `obj_starwalker_offswitch`,
  `obj_sumarker`, `obj_trigger`, `obj_waterable_flower_2x2`,
  `obj_wateringcan_pedestal`.
- Incoming transitions: door from room_dw_garden_enemyrush; door from
  room_dw_garden_firstdash; door from room_dw_garden_flowerygardening.
- Outgoing transitions: to room_dw_garden_enemyrush; to
  room_dw_garden_firstdash; to room_dw_garden_flowerygardening.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_starwalkerdash`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bulletarea`, `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_garden_starwalkerdash`, `obj_genmarker`, `obj_grassanim_new`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_bird_new`,
  `obj_overworld_dashbullet_spawner`, `obj_parallaxer`, `obj_plat_game`,
  `obj_plat_loopboundary`, `obj_sdl_dark`, `obj_sdr_dark`,
  `obj_solidblocksized`, `obj_starwalker_offswitch`, `obj_sul_dark`,
  `obj_sur_dark`, `obj_torigate_dash`, `obj_waterpit`, `obj_waterreflect`.
- Incoming transitions: door from room_dw_garden_platshortcut.
- Outgoing transitions: to room_dw_garden_platshortcut.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_susiechase`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_darkslide_new`,
  `obj_doorAny`, `obj_dw_garden_susiechase`, `obj_floorswitch`,
  `obj_grassanim_new`, `obj_mainchara`, `obj_markerAny`, `obj_musicer_garden`,
  `obj_parallax_garden_flower_lights`, `obj_pushable_block`, `obj_sdl`,
  `obj_solidblocksized`, `obj_solidblocksized_alt`, `obj_solidenemy`,
  `obj_starwalker_offswitch`, `obj_sur`, `obj_trigger`.
- Incoming transitions: door from room_dw_garden_hardpressureplates.
- Outgoing transitions: to room_dw_garden_hardpressureplates.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_video`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_room_garden_video`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_garden_wateringcan_aqua`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_depthsorter`, `obj_doorAny`, `obj_dw_garden_wateringcan_aqua`,
  `obj_genmarker`, `obj_grassanim_new`, `obj_item_knock_off_bar`,
  `obj_layer_to_waterable_assets`, `obj_mainchara`, `obj_markerAny`,
  `obj_musicer_room`, `obj_plat_game`, `obj_solidblocksized`,
  `obj_treasure_room`, `obj_trigger`, `obj_waterable_flower_cluster`,
  `obj_waterable_grass`, `obj_wateringcan_pedestal`.
- Incoming transitions: door from room_dw_garden_aqua; door from
  room_dw_garden_aquatransition.
- Outgoing transitions: to room_dw_garden_aqua; to
  room_dw_garden_aquatransition.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_petaltest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_blocktree_bg`, `obj_blocktree_pink_bg`,
  `obj_camera_clamper`, `obj_darkcontroller`,
  `obj_dw_garden_shearyencounter_waves`, `obj_grassanim_new`, `obj_mainchara`,
  `obj_markerAny`, `obj_pinktree`, `obj_sakurafubuki_mini`,
  `obj_spinpetalmaker`, `obj_waterreflect`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_pink_encounter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_castlereflect`, `obj_darkcontroller`,
  `obj_depthsorter`, `obj_doorAny`, `obj_dw_pink_encounter`, `obj_leafpetals`,
  `obj_mainchara`, `obj_markerAny`, `obj_solidblocksized`.
- Incoming transitions: door from room_dw_fcastle_pinkroom.
- Outgoing transitions: to room_dw_fcastle_pinkroom.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_post_flowery_battle`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_fcastle_post_flowery_battle`, `obj_mainchara`, `obj_markerAny`,
  `obj_parallax_cliffs`, `obj_post_flowery_battle`, `obj_solidblockDark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_dw_fcastle_top_fountain.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_post_fountain_close`

- Area: Area not established.
- Runtime role/status: Dark Fountain event or presentation controlled by its
  placed fountain controller; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_dw_post_fountain_close`,
  `obj_krmarker`, `obj_mainchara`, `obj_markerAny`, `obj_ramarker`,
  `obj_sumarker`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_ralsei_castle_1f`

- Area: Castle Town.
- Runtime role/status: Ralsei castle first floor; verified production reachable.
- Important controllers: `obj_castle_cauldron_glow`, `obj_darkcontroller`,
  `obj_doorA`, `obj_doorW`, `obj_mainchara`, `obj_markerB`, `obj_markerw`,
  `obj_markerX`, `obj_readable_room1`, `obj_room_castle_1f`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_ralsei_castle_2f`

- Area: Castle Town.
- Runtime role/status: Ralsei castle second floor; verified production
  reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerAny`, `obj_markerv`,
  `obj_markerw`, `obj_room_castle_2f`, `obj_soliddark`.
- Incoming transitions: door from room_dw_ralsei_castle_3f; runtime dispatch;
  runtime dispatch.
- Outgoing transitions: to room_dw_ralsei_castle_3f.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_ralsei_castle_3f`

- Area: Castle Town.
- Runtime role/status: Ralsei castle third floor; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_musicer_darkcastle`, `obj_room_castle_3f`,
  `obj_solidblockDark`.
- Incoming transitions: door from room_dw_castle_rooms_ralsei; door from
  room_dw_ralsei_castle_2f; door from room_dw_ralsei_castle_basketball; door
  from room_dw_ralsei_castle_basketball.
- Outgoing transitions: to room_dw_castle_rooms_ralsei; to
  room_dw_ralsei_castle_2f; to room_dw_ralsei_castle_basketball; to
  room_dw_ralsei_castle_basketball.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_ralsei_castle_basketball`

- Area: Castle Town.
- Runtime role/status: Ralsei castle basketball room; verified production
  reachable.
- Important controllers: `obj_darkcontroller`, `obj_doorAny`,
  `obj_dw_ralsei_castle_basketball`, `obj_mainchara`, `obj_markerAny`,
  `obj_solidblocksized`, `obj_solidblocksized_alt`, `obj_solidenemy`.
- Incoming transitions: door from room_dw_ralsei_castle_3f; door from
  room_dw_ralsei_castle_3f.
- Outgoing transitions: to room_dw_ralsei_castle_3f; to
  room_dw_ralsei_castle_3f.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_ralsei_castle_front`

- Area: Castle Town.
- Runtime role/status: Ralsei castle front; verified production reachable.
- Important controllers: `obj_castle_torch`, `obj_darkcontroller`, `obj_doorB`,
  `obj_doorW`, `obj_mainchara`, `obj_markerA`, `obj_markerX`,
  `obj_room_castle_front`, `obj_soliddark`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_rhythm`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_rhythmgame`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_rhythm_countdown`

- Area: Rhythm subsystem.
- Runtime role/status: border/tension handling includes this countdown room; no
  ingress transition verified; verified production reachable.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_room_rhythm_countdown`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_dw_rhythm_empty`

- Area: Rhythm subsystem.
- Runtime role/status: empty rhythm staging/template asset; no runtime dispatch
  verified; uncertain-no-ingress.
- Important controllers: `none placed or creation-code-created`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_ed`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_credits_ch5`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_empty`

- Area: Template.
- Runtime role/status: empty room template/bootstrap asset; no production
  ingress asserted; bootstrap.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 5: `room_floortex_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_dw_garden_aquahole_left`,
  `obj_mainchara`, `obj_markerAny`, `obj_musicer_bird_new`,
  `obj_plat_autoblock`, `obj_plat_block`, `obj_plat_floortex_BACK`,
  `obj_plat_floortex_FLOOR`, `obj_plat_floortex_FLOOR_AlignBottom1TILE`,
  `obj_plat_floortex_FRONT`, `obj_plat_floortex_Yorigin`,
  `obj_plat_floortex_Yplat`, `obj_plat_game`, `obj_platmode_recolor`,
  `obj_platswap`, `obj_platswap_statue`, `obj_shortcut_door`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_flowershop_1f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_doorX`, `obj_mainchara`,
  `obj_markerAny`, `obj_markerX`, `obj_overworldc`, `obj_room_flowershop_1f`,
  `obj_solidblock`, `obj_sul`, `obj_sur`.
- Incoming transitions: door from room_flowershop_2f; door from
  room_flowershop_2f; runtime dispatch.
- Outgoing transitions: to room_flowershop_2f; to room_flowershop_2f.
- Conditions: No additional condition verified.

### Chapter 5: `room_flowershop_2f`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_mainchara`, `obj_markerAny`,
  `obj_overworldc`, `obj_room_flowershop_2f`, `obj_solidblock`.
- Incoming transitions: door from room_flowershop_1f; door from
  room_flowershop_1f; runtime dispatch.
- Outgoing transitions: to room_flowershop_1f; to room_flowershop_1f.
- Conditions: No additional condition verified.

### Chapter 5: `room_gameover`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_gameover_init`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_gif_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_sprite_catalog`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_gms_debug_failsafe`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_gamecontroller`, `obj_gms_debug_failsafe`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `room_GMS2_test`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_chaseenemy`, `obj_darkcontroller`,
  `obj_mainchara`, `obj_soliddark`, `obj_swordarea`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_graveyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_markerX`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_sur`, `obj_town_event`, `obj_town_graveyard`.
- Incoming transitions: returning Light World door/controller flow in runtime
  controller; placed overworld controller and room-specific event objects.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_hospital_hallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorB`, `obj_doorC`, `obj_mainchara`,
  `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: returning Light World door/controller flow in runtime
  controller; placed overworld controller and room-specific event objects.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_hospital_lobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorW`, `obj_mainchara`,
  `obj_markerB`, `obj_markerw`, `obj_npc_room`, `obj_overworldc`,
  `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_hospital_room2`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`.
- Incoming transitions: returning Light World door/controller flow in runtime
  controller; placed overworld controller and room-specific event objects.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_hospital_rudy`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_npc_rudy`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_hospital`, `obj_solidblock`.
- Incoming transitions: returning Light World door/controller flow in runtime
  controller; placed overworld controller and room-specific event objects.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `ROOM_INITIALIZE`

- Area: Bootstrap.
- Runtime role/status: runtime initialization room; bootstrap.
- Important controllers: `obj_debugProfiler`, `obj_gamecontroller`,
  `obj_initializer2`.
- Incoming transitions: startup/bootstrap asset; no additional dispatch
  condition verified.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: bootstrap dispatch.

### Chapter 5: `room_insidecloset`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_intro_ch5`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_intro_ch5`.
- Incoming transitions: runtime variable dispatch to room_intro_ch5; runtime
  variable dispatch to room_intro_ch5.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_krishallway`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_doorC`, `obj_hallway_mirror`,
  `obj_mainchara`, `obj_markerA`, `obj_markerD`, `obj_overworldc`,
  `obj_readable_room1`, `obj_room_krishallway`, `obj_solidblock`,
  `obj_solidlong`.
- Incoming transitions: door from room_krisroom.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_krisroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_krisroom`, `obj_mainchara`,
  `obj_markerB`, `obj_overworldc`, `obj_room_krisroom`, `obj_solidblock`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_krishallway.
- Conditions: No additional condition verified.

### Chapter 5: `room_legend`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_legend`.
- Incoming transitions: runtime variable dispatch to room_legend; runtime
  variable dispatch to room_legend.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_legend_neo`

- Area: Development.
- Runtime role/status: Sunkus-key debug Legend destination from obj_mainchara
  input; uncertain-no-ingress.
- Important controllers: `obj_legend_neo`.
- Incoming transitions: debug/test runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_lerptest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_lerptest`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_library`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorW`, `obj_doorX`,
  `obj_mainchara`, `obj_markert`, `obj_markerw`, `obj_markerX`,
  `obj_npc_facing`, `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`,
  `obj_solidblock`, `obj_town_library`.
- Incoming transitions: runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_church_choir`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworldc`, `obj_room_church_choir`,
  `obj_solidblockLight`.
- Incoming transitions: door from room_lw_church_entrance.
- Outgoing transitions: to room_lw_church_entrance.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_church_entrance`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_church_entrance`,
  `obj_church_entrance_foreground`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworldc`, `obj_solidblockLight`,
  `obj_solidblocksized`, `obj_sul`, `obj_sur`.
- Incoming transitions: door from room_lw_church_choir; door from
  room_lw_church_main; door from room_lw_church_office; door from
  room_town_church.
- Outgoing transitions: to room_lw_church_choir; to room_lw_church_main; to
  room_lw_church_office; to room_town_church.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_church_main`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworldc`, `obj_room_church_main`,
  `obj_solidblockLight`, `obj_sul`, `obj_sur`.
- Incoming transitions: door from room_lw_church_entrance.
- Outgoing transitions: to room_lw_church_entrance.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_church_office`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworldc`, `obj_room_church_office`,
  `obj_solidblockLight`.
- Incoming transitions: door from room_lw_church_entrance.
- Outgoing transitions: to room_lw_church_entrance.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_computer_lab`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorW`, `obj_mainchara`,
  `obj_markerw`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_conbini`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorw_musfade`,
  `obj_mainchara`, `obj_markerv`, `obj_musicer_conbini`, `obj_npc_conbini`,
  `obj_npc_room`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_icee_pizza`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorW`, `obj_mainchara`,
  `obj_markert`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_soliddark`, `obj_town_pizza`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_library_upstairs`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorW`, `obj_mainchara`, `obj_markert`,
  `obj_npc_library_upstairs`, `obj_overworldc`, `obj_readable_room1`,
  `obj_sdl_dark`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_noellehouse_dess`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_mainchara`, `obj_markerAny`,
  `obj_noellehouse_dess`, `obj_overworldc`, `obj_solidblockLight`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_lw_police`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_mainchara`, `obj_markerv`,
  `obj_npc_police`, `obj_overworldc`, `obj_readable_room1`, `obj_soliddark`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: to room_town_south.
- Conditions: No additional condition verified.

### Chapter 5: `room_man`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_blocktree_bg`, `obj_darkcontroller`,
  `obj_doorAny`, `obj_mainchara`, `obj_markerAny`, `obj_room_man`,
  `obj_soliddark`.
- Incoming transitions: door from room_dw_dogballoon.
- Outgoing transitions: to room_dw_cliff_seth_miniboss.
- Conditions: No additional condition verified.

### Chapter 5: `room_overworldBulletEnemyTest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_darkcontroller`, `obj_mainchara`,
  `obj_overworld_bulletarea`, `obj_solidblocksized`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_plat_lab`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_blend_test`, `obj_darkcontroller`,
  `obj_debug_hotkeys`, `obj_enemy_wave`, `obj_flower_death_tester`,
  `obj_mainchara`, `obj_object_resetter`, `obj_plat_cam_clampzone`,
  `obj_plat_combatstarter`, `obj_plat_enm_aqua_sword`, `obj_plat_enm_bigtome`,
  `obj_plat_enm_glovespawner`, `obj_plat_enm_gun`, `obj_plat_enm_yellow_ufohat`,
  `obj_plat_floor`, `obj_plat_floortex_FLOOR`, `obj_plat_floortex_FRONT`,
  `obj_plat_game`, `obj_plat_orangewall`, `obj_platswap`, `obj_platswap_statue`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_rhythmgame_editor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_rhythmgame_editor`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_school_unusedroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_doorD`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_solidblock`, `obj_sul`,
  `obj_unusedclassevent`.
- Incoming transitions: non-production unused classroom; excluded from ordered
  adjacency and only referenced by unused/fountain cleanup/readable-room
  compatibility code.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_schooldoor`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_darkdoor`, `obj_doorC`, `obj_doorD`,
  `obj_mainchara`, `obj_markerC`, `obj_markerD`, `obj_markerX`,
  `obj_overworldc`, `obj_readable_room1`, `obj_room_schooldoor`,
  `obj_solidblock`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_schoollobby`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorAny`, `obj_doorB`, `obj_doorC`,
  `obj_mainchara`, `obj_markerA`, `obj_markerB`, `obj_markerD`, `obj_markerX`,
  `obj_overworldc`, `obj_readable_room1`, `obj_room_schoollobby`,
  `obj_solidblock`, `obj_sul`.
- Incoming transitions: door from room_town_school; runtime dispatch; runtime
  dispatch; runtime dispatch.
- Outgoing transitions: to room_town_school.
- Conditions: No additional condition verified.

### Chapter 5: `room_shop_ch5`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop_ch5`.
- Incoming transitions: door from room_dw_cliff_shop.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_shop_music`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop_music`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_shop1`

- Area: Area not established.
- Runtime role/status: Shop interface driven by its placed shop controller;
  verified production reachable.
- Important controllers: `obj_shop1`.
- Incoming transitions: door from room_dw_castle_town; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_sound_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_soundtester`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_sprite_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_spritecomparer`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_title_placeholder`

- Area: Development.
- Runtime role/status: debug/test harness or developer dispatch destination;
  debug-test.
- Important controllers: `obj_title_placeholder`.
- Incoming transitions: runtime variable dispatch to room_title_placeholder.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: debug input.

### Chapter 5: `room_torbathroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorB`, `obj_mainchara`, `obj_markerA`,
  `obj_overworldc`, `obj_room_torbathroom`, `obj_solidblock`, `obj_sul`,
  `obj_sur`.
- Incoming transitions: returning Light World room-specific controller/overworld
  staging with ordered room route ordered route context.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_torhouse`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorA`, `obj_doorD`, `obj_doorX_musfade`,
  `obj_mainchara`, `obj_markerB`, `obj_markerC`, `obj_markerX`,
  `obj_musicer_gen`, `obj_overworldc`, `obj_room_torhouse`, `obj_sdl`,
  `obj_sdr`, `obj_solidblock`, `obj_solidlong`, `obj_sul`, `obj_sur`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_torielclass`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_mainchara`,
  `obj_markerB`, `obj_overworldc`, `obj_readable_room1`, `obj_room_torielclass`,
  `obj_solidblock`, `obj_torielclass_event`.
- Incoming transitions: returning Light World room-specific controller/overworld
  staging with ordered room route ordered route context.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_torroom`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: returning Light World room-specific controller/overworld
  staging with ordered room route ordered route context.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_towery_tester`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; uncertain-no-ingress.
- Important controllers: `obj_debug_hotkeys`, `obj_flowery_towery`.
- Incoming transitions: no production ingress discovered.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_apartments`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: returning Light World room-specific controller/overworld
  staging with ordered room route ordered route context.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_church`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_church_event`,
  `obj_depthsorter_lw`, `obj_doorA`, `obj_doorAny`, `obj_doorC_musfade`,
  `obj_doorD`, `obj_doorX`, `obj_eveningshadowfull`, `obj_festival_confetti`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerB`, `obj_markerC`, `obj_markerD`,
  `obj_markerX`, `obj_overworldc`, `obj_room_town_church`, `obj_sdl`, `obj_sdr`,
  `obj_solidblock`, `obj_soliddark`.
- Incoming transitions: door from room_lw_church_entrance; runtime dispatch.
- Outgoing transitions: to room_lw_church_entrance.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_krisyard`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorC`, `obj_doorX_musfade`,
  `obj_eveningshadowfull`, `obj_mainchara`, `obj_markerD`, `obj_markerX`,
  `obj_musicer_town`, `obj_npc_sign`, `obj_overworldc`,
  `obj_room_town_krisyard`, `obj_sdl`, `obj_sdr`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_mid`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorC`, `obj_doorD`,
  `obj_doorW`, `obj_doorw_musfade`, `obj_doorX`, `obj_eveningshadowfull`,
  `obj_festival_animator`, `obj_festival_bulb`, `obj_festival_confetti`,
  `obj_mainchara`, `obj_markerC`, `obj_markerD`, `obj_markert`, `obj_markerv`,
  `obj_markerw`, `obj_markerX`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_mid`, `obj_solidblock`, `obj_solidblockLight`.
- Incoming transitions: runtime dispatch; runtime dispatch; runtime dispatch;
  runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_noellehouse`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_givedepth`, `obj_doorAny`, `obj_mainchara`,
  `obj_markerAny`, `obj_overworldc`, `obj_room_town_noellehouse`,
  `obj_solidblockLight`, `obj_sur`.
- Incoming transitions: door from room_town_north; runtime dispatch.
- Outgoing transitions: to room_town_north.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_north`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_bg_palette_swap`, `obj_doorA`, `obj_doorAny`,
  `obj_doorC`, `obj_doorD`, `obj_doorX`, `obj_eveningshadowfull`,
  `obj_festival_animator`, `obj_festival_bulb`, `obj_festival_confetti`,
  `obj_mainchara`, `obj_markerAny`, `obj_markerB`, `obj_markerC`, `obj_markerD`,
  `obj_markerX`, `obj_musicer_town`, `obj_noellehouse_fence`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdl_dark`, `obj_sdr`, `obj_solidblock`,
  `obj_solidblockLight`, `obj_sul`, `obj_sur`, `obj_town_north`.
- Incoming transitions: door from room_town_noellehouse; runtime dispatch;
  runtime dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_town_noellehouse.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_northwest`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_mainchara`, `obj_overworldc`.
- Incoming transitions: returning Light World room-specific controller/overworld
  staging with ordered room route ordered route context.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_school`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorAny`, `obj_doorB`, `obj_eveningshadowfull`,
  `obj_mainchara`, `obj_markerA`, `obj_markerX`, `obj_musicer_town`,
  `obj_overworldc`, `obj_room_town_school`, `obj_sdr`, `obj_solidblock`.
- Incoming transitions: door from room_schoollobby; runtime dispatch; runtime
  dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: to room_schoollobby.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_shelter`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorD_musfade`, `obj_mainchara`, `obj_markerC`,
  `obj_overworldc`, `obj_readable_room1`, `obj_room_town_shelter`, `obj_sdl`,
  `obj_sdr`, `obj_solidblock`, `obj_sul`, `obj_sur`, `obj_town_shelter_event`.
- Incoming transitions: returning Light World door/controller flow in runtime
  controller; placed overworld controller and room-specific event objects.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_town_south`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_84_lang_helper`, `obj_doorA`, `obj_doorC`,
  `obj_doorD`, `obj_doorW`, `obj_doorX`, `obj_eveningshadowfull`,
  `obj_festival_bulb`, `obj_festival_confetti`, `obj_mainchara`, `obj_markerB`,
  `obj_markerC`, `obj_markerD`, `obj_markerv`, `obj_markerw`, `obj_markerX`,
  `obj_musicer_town`, `obj_overworldc`, `obj_readable_room1`,
  `obj_room_town_south`, `obj_solidblock`, `obj_solidblockLight`, `obj_sul`,
  `obj_town_event`.
- Incoming transitions: door from room_lw_police; runtime dispatch; runtime
  dispatch; runtime dispatch; runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

### Chapter 5: `room_townhall`

- Area: Area not established.
- Runtime role/status: Purpose not established from verified room-local or
  transition evidence; verified production reachable.
- Important controllers: `obj_doorX`, `obj_mainchara`, `obj_markerX`,
  `obj_npc_room`, `obj_npc_room_animated`, `obj_overworldc`,
  `obj_readable_room1`, `obj_sdl`, `obj_solidblock`.
- Incoming transitions: runtime dispatch.
- Outgoing transitions: no literal doorRoom edge discovered.
- Conditions: No additional condition verified.

## Runtime and Modding Notes

See [Overworld Runtime](overworld.md), [Cutscene System](cutscene-system.md),
and [Dialogue System](dialogue-system.md).
