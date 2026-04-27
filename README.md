# sudo_project_iolog_write_info_file_legacy_NULL_Pointer_Dereference

sudo logsrvd NULL Pointer Dereference (DoS)
Target: sudo 1.9.17 logsrvd (port 30343)
CWE-476: NULL Pointer Dereference

VULNERABILITY:
  logsrvd does not properly validate the runargv pointer after allocation failure.
  When AcceptMessage is sent WITHOUT runargv field, the pointer remains NULL and
  causes segmentation fault when attempting to access runargv[1].

IMPACT:
  - Remote Denial of Service (server crash)
  - No authentication required
  - Trivial exploit (2 protobuf messages)

EXPLOITABILITY:
  - CVSS 3.1: 7.5 (HIGH)
  - Vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:H
  - Complexity: LOW
  - Privileges: NONE

AUTHOR: Pedro Henrique de Almeida Silva <psilva@stacksec.com.br>
ORGANIZATION: Stack Security Intelligence Research Team
WEBSITE: https://vanalyze.io
DATE: 2026-02-21


PATCHED IN https://github.com/sudo-project/sudo/commit/e1fad8affe215e402dcaebf3e93bf82c6339afab
