# MSME Readiness Agent — downloads

Released installers of the MSME Readiness Agent, a Windows program that reads machine
data read-only on an MSME's shop floor and reports the enterprise's readiness against
line items of Indian government publications: ZED certification, the MSME Competitive
(Lean) Scheme, BEE energy guidance, NPC Bharat 4.0, NPC's smart-manufacturing kit
requirements, and state electricity tariff orders. Every line item names its document,
edition, page and web address. It reports readiness; it does not certify.

This repository holds no source code. It is written to by the publisher's release
procedure only.

## Install

1. Open the [latest release](https://github.com/selfevolvia/msme-readiness-agent-releases/releases/latest)
   and download `MsmeReadinessAgent-x.y.z.msi` and `SHA256SUMS.txt`.
2. Check the file before running it. In PowerShell, in the download folder:

   ```powershell
   (Get-FileHash .\MsmeReadinessAgent-x.y.z.msi -Algorithm SHA256).Hash.ToLower()
   ```

   The result must equal the line for that file in `SHA256SUMS.txt`.
3. Run the installer as an administrator and accept the licence terms. The installer is
   not code-signed yet, so Windows shows "Windows protected your PC": choose
   **More info → Run anyway**, and only after step 2.
4. Open **MSME Readiness Agent** from the Start menu (`http://127.0.0.1:8750/`) and
   follow Setup.

Windows 10, Windows 11 or Windows Server 2019 and later, 64-bit. The six guideline
packs are inside the installer; the `.gpack` files of a release are for adding a newer
pack to an installed program (Setup → Guideline packs).

## Handbooks

Each release carries four PDF handbooks: `msme-handbook.pdf` and `officer-handbook.pdf`
in English, and `msme-handbook.hi.pdf` and `officer-handbook.hi.pdf` in Hindi. The MSME
handbook covers installing, connecting machines and SCADA, and reading the report. The
officer handbook lists every government document the packs were compiled from.

## Update notice

The program never installs anything by itself. To let it say that a newer version
exists, an administrator sets the machine environment variable
`Agent__UpdateManifestUrl` to

```
https://raw.githubusercontent.com/selfevolvia/msme-readiness-agent-releases/main/release-manifest.json
```

and restarts the `MsmeReadinessAgent` service. The manifest is signed with the same
publisher key as the guideline packs; the program ignores one that is not.

## Licence

Use of the program is under [LICENSE.txt](LICENSE.txt). The licences of the
third-party software it contains are in `THIRD-PARTY-NOTICES.md` of each release.
