<div align="center">

⛅ &nbsp; **r2-release-action** &nbsp; ⛅

store versioned binaries in cloudflare r2

</div>

## getting started

```yaml
-   name: 💝 Deploy prebuilts 💝
    uses: rarestype/r2-release-action@v1
    with:
        from: .build/release
        include: |
            product-a
            product-b
        project: your-project
        version: ${{ inputs.version }}
        archive: products.tar.gz
        bucket: your-bucket
```

the `from` and `project` arguments may be omitted, and will default to `.build/release` and the name of the calling repository, respectively.

by default, one archive will be created containing all `include` paths. to upload *separate* archives instead, omit `archive` and use the `each` parameter instead to select the archive format.

```yaml
-   name: 💝 Deploy prebuilts 💝
    uses: rarestype/r2-release-action@v1
    with:
        from: .build/release
        each: tar.gz # or 'zip'
        include: |
            product-a
            product-b
        project: your-project
        version: ${{ inputs.version }}
        bucket: your-bucket
```
