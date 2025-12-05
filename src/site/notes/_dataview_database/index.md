---
{"date":null,"source":"dataview","tags":["dataview","index"],"title":"Dataview queries","type":"index","URL":"https://blacksmithgu.github.io/obsidian-dataview/","dg-publish":true,"permalink":"/dataview-database/index/","dgPassFrontmatter":true}
---


# Dataview queries

><span style="color: orange; font-size:12">For these lists to display correct information you need to install `dataview` plugin</span>

## Notes with "draft" status

Below is a `dataview` query that returns a table of notes where  `status`:`draft`.
_Switch to edit mode to see the actual query and the comments explaining the syntax._

| File                                                                                                                     | status | modified           |
| ------------------------------------------------------------------------------------------------------------------------ | ------ | ------------------ |
| [[00_Fleeting_inbox/Docker\|Docker]]                                                                                  | draft  | December 05, 2025  |
| [[00_Fleeting_inbox/freelancing\|freelancing]]                                                                        | draft  | December 05, 2025  |
| [[00_Fleeting_inbox/git workflows\|git workflows]]                                                                    | draft  | December 05, 2025  |
| [[00_Fleeting_inbox/http and the web\|http and the web]]                                                              | draft  | December 05, 2025  |
| [[00_Fleeting_inbox/interesting quotes\|interesting quotes]]                                                          | draft  | December 05, 2025  |
| [[00_Fleeting_inbox/job hunting for junior devs\|job hunting for junior devs]]                                        | draft  | December 05, 2025  |
| [[01_Reference/curl\|curl]]                                                                                           | draft  | December 05, 2025  |
| [[01_Reference/fzf\|fzf]]                                                                                             | draft  | December 05, 2025  |
| [[01_Reference/google search\|google search]]                                                                         | draft  | December 05, 2025  |
| [[01_Reference/javascript notes\|javascript notes]]                                                                   | draft  | December 05, 2025  |
| [[01_Reference/react notes\|react notes]]                                                                             | draft  | December 05, 2025  |
| [[01_Reference/tar archive\|tar archive]]                                                                             | draft  | December 05, 2025  |
| [[01_Reference/ux-ui design, figma\|ux-ui design, figma]]                                                             | draft  | December 05, 2025  |
| [[01_Reference/zakon o policijskim poslovima i ovlastima\|zakon o policijskim poslovima i ovlastima]]                 | draft  | December 05, 2025  |
| [[02_Ideas_and_projects/ideas/Singularity\|Singularity]]                                                              | draft  | December 05, 2025  |
| [[02_Ideas_and_projects/ideas/deluxe static web\|deluxe static web]]                                                  | draft  | December 05, 2025  |
| [[02_Ideas_and_projects/ideas/family integration for elders\|family integration for elders]]                          | draft  | December 05, 2025  |
| [[02_Ideas_and_projects/projects/_dev_tools/LLM/bootstrap LLM environment\|bootstrap LLM environment]]                | draft  | December 05, 2025  |
| [[02_Ideas_and_projects/projects/_dev_tools/LLM/instructions\|instructions]]                                          | draft  | December 05, 2025  |
| [[02_Ideas_and_projects/projects/course_react/instructions\|instructions]]                                            | draft  | December 05, 2025  |
| [[03_Literature_notes/McMafia\|McMafia]]                                                                              | draft  | December 05, 2025  |
| [[03_Literature_notes/domovinski rat - rat prije rata\|domovinski rat - rat prije rata]]                              | draft  | December 05, 2025  |
| [[03_Literature_notes/grokking web application security\|grokking web application security]]                          | draft  | December 05, 2025  |
| [[03_Literature_notes/javascript - the definitive guide\|javascript - the definitive guide]]                          | draft  | December 05, 2025  |
| [[03_Literature_notes/learning typecript\|learning typecript]]                                                        | draft  | December 05, 2025  |
| [[03_Literature_notes/react key concepts - an in-depth guide\|react key concepts - an in-depth guide]]                | draft  | December 05, 2025  |
| [[03_Literature_notes/the science of self-discipline\|the science of self-discipline]]                                | draft  | December 05, 2025  |
| [[06_Religija/bible quotes\|bible quotes]]                                                                            | draft  | December 05, 2025  |
| [[06_Religija/devotional_reading/god presence in the dark seasons of life\|god presence in the dark seasons of life]] | draft  | December 05, 2025  |
| [[06_Religija/devotional_reading/nasljeduj krista\|nasljeduj krista]]                                                 | draft  | December 05, 2025  |
| [[06_Religija/expressions/from logic to belief\|from logic to belief]]                                                | draft  | December 05, 2025  |
| [[06_Religija/katekizam katolicke crkve\|katekizam katolicke crkve]]                                                  | draft  | December 05, 2025  |
| [[06_Religija/todo\|todo]]                                                                                            | draft  | December 05, 2025  |
| [[03_Literature_notes/linux command line and shell scripting bible\|linux command line and shell scripting bible]]    | draft  | December 05, 2025  |
| [[03_Literature_notes/learning react - modern patterns 2nd edition\|learning react - modern patterns 2nd edition]]    | draft  | December 05, 2025  |
| [[03_Literature_notes/how to take smart notes\|how to take smart notes]]                                              | draft  | December 05, 2025  |
| [[03_Literature_notes/building a second brain\|building a second brain]]                                              | draft  | December 05, 2025  |
| [[03_Literature_notes/books to read\|books to read]]                                                                  | draft  | December 05, 2025  |
| [[03_Literature_notes/modern fullstack react projects\|modern fullstack react projects]]                              | draft  | December 05, 2025  |
| [[_templates/scripts_template\|scripts_template]]                                                                     | draft  | November 29, 2025  |
| [[_scripts/_templater_docs\|_templater_docs]]                                                                         | draft  | November 05, 2025  |
| [[02_Ideas_and_projects/projects/_dev_tools/LLM/writing agents\|writing agents]]                                      | draft  | September 08, 2025 |
| [[02_Ideas_and_projects/ideas/portable system configuration\|portable system configuration]]                          | draft  | August 05, 2025    |
| [[02_Ideas_and_projects/ideas/personal chatbot\|personal chatbot]]                                                    | draft  | July 30, 2025      |
| [[00_Fleeting_inbox/neurotransmitters\|neurotransmitters]]                                                            | draft  | February 10, 2025  |

{ .block-language-dataview}

## Other index notes

Below is a dataview query that returns a table of notes where `type`:`index` and beside the filename it shows the root directory by splitting the full path into array at each "/" than returning the first item from the array which should be the root directory.
_Switch to edit mode to see the actual query and the comments explaining the syntax._

| File                                                                                                      | title                                               | Root directory        |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------- | --------------------- |
| [[03_Literature_notes/books to read\|books to read]]                                                   | Books to read                                       | 03_Literature_notes   |
| [[02_Ideas_and_projects/projects/_dev_tools/LLM/bootstrap LLM environment\|bootstrap LLM environment]] | Bootstrap the environment for Large Language Models | 02_Ideas_and_projects |
| [[06_Religija/index\|index]]                                                                           | I am a Christian                                    | 06_Religija           |
| [[06_Religija/todo\|todo]]                                                                             | TODO index                                          | 06_Religija           |

{ .block-language-dataview}

## Other dataview queries

Below is a `dataview` query that returns a list of notes containing the #dataview and #index tags.
_Switch to edit mode to see the actual query and the comments explaining the syntax._

- [[_dataview_database/properties - type values\|properties - type values]]
- [[_dataview_database/properties - tags values\|properties - tags values]]
- [[_dataview_database/properties - status property\|properties - status property]]
- [[_dataview_database/properties - source values\|properties - source values]]
- [[_dataview_database/properties - available keys\|properties - available keys]]
- [[_dataview_database/index\|index]]

{ .block-language-dataview}

## Reference

- [[01_Reference/dataview\|dataview]] - personal note
- [[_workflow\|Workflow explanation]] - personal note
- [blacksmithgu.github/documentation](https://blacksmithgu.github.io/obsidian-dataview/) - official documentation
- [blacksmithgu.github/resources](https://blacksmithgu.github.io/obsidian-dataview/resources/resources-and-support/) - community resources
- [publish.obsidian.md/hub](https://publish.obsidian.md/hub/00+-+Start+here) - "Obsidian hub", community guides, workflows and courses
- [publish.obsidian.md/community_guides](https://publish.obsidian.md/hub/04+-+Guides%2C+Workflows%2C+%26+Courses/Guides/An+Introduction+to+Dataview) - "SkepticMystic's textual guide"
- [publish.obsidian.md/community_guides](https://publish.obsidian.md/hub/04+-+Guides%2C+Workflows%2C+%26+Courses/Community+Talks/YT+-+An+Introduction+to+Dataview) - "SkepticMystic's video guide"
