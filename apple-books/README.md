# Apple Books Upload Packages

## Quick Start

1. **Create book listings** at https://authors.apple.com
2. **Get Apple IDs** for each book from App Store Connect
3. **Update metadata.xml** in each .itmsp folder with the Apple ID
4. **Upload via Transporter CLI** (commands below)

## Package Contents

```
apple-books/
├── playbook.itmsp/
│   ├── metadata.xml          # Edit: add apple_id
│   └── Purple_Squirrel_Playbook.epub
├── nutshell.itmsp/
│   ├── metadata.xml          # Edit: add apple_id
│   └── Purple_Squirrel_Nutshell.epub
└── cookbook.itmsp/
    ├── metadata.xml          # Edit: add apple_id
    └── Purple_Squirrel_Cookbook.epub
```

## Step 1: Get Apple IDs

1. Go to https://authors.apple.com or https://appstoreconnect.apple.com
2. Create new book for each title
3. Copy the Apple ID (numeric) from the book details

## Step 2: Update metadata.xml

In each .itmsp folder, edit `metadata.xml` and replace:
```xml
<apple_id>YOUR_APPLE_ID_HERE</apple_id>
```
with the actual Apple ID, e.g.:
```xml
<apple_id>1234567890</apple_id>
```

## Step 3: Validate Packages

```bash
# Validate before uploading
/Applications/Transporter.app/Contents/itms/bin/iTMSTransporter \
  -m verify \
  -f playbook.itmsp \
  -v detailed
```

## Step 4: Upload Packages

```bash
# Upload Playbook
/Applications/Transporter.app/Contents/itms/bin/iTMSTransporter \
  -m upload \
  -f playbook.itmsp \
  -v detailed

# Upload Nutshell
/Applications/Transporter.app/Contents/itms/bin/iTMSTransporter \
  -m upload \
  -f nutshell.itmsp \
  -v detailed

# Upload Cookbook
/Applications/Transporter.app/Contents/itms/bin/iTMSTransporter \
  -m upload \
  -f cookbook.itmsp \
  -v detailed
```

## Metadata Fields

| Field | Value |
|-------|-------|
| Provider | MatthewKarsten172794014891 |
| Price (US) | $9.99 |
| Price (UK) | £7.99 |
| Price (EU) | €8.99 |
| Territory | Worldwide |
| Language | English |

## Troubleshooting

- **Authentication errors**: Run `open -a Transporter` and sign in via GUI first
- **Validation errors**: Check EPUB structure with Apple's Books Asset Guide
- **Missing Apple ID**: Create book listing in App Store Connect first

## Resources

- [Apple Books for Authors](https://authors.apple.com)
- [Transporter User Guide](https://help.apple.com/itc/transporteruserguide/)
- [Apple Books Asset Guide](https://help.apple.com/itc/booksassetguide/)
