# dym — kho bundle `/doyourmagic` đã chạy

Mỗi thư mục là **một lượt chạy thật** của skill [`doyourmagic`](https://github.com/Rheinmir/setup/tree/orca/skills/doyourmagic) trên một repo ngoài: đã clone, đọc manifest/parser, chạy thử trong sandbox, đo mã thoát, rồi viết thành workflow **gõ được**. Kéo về dùng thay vì chạy lại từ đầu.

| Bundle | Repo gốc | Dạng | Gồm |
|---|---|---|---|
| [`setup/`](setup/) | [rheinmir/setup](https://github.com/Rheinmir/setup) (overstack) | **skill** — hub `dym-setup` + 6 sub-skill | `workflows.md` · `flow.html` · `skills/` |
| [`impeccable/`](impeccable/) | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | doc (dạng cũ `NN-*.md`, chưa chuyển sang skill) | `workflows.md` · `index.html` · 7 doc |

## Dùng

**Cách 1 — cài như skill (chỉ nạp khi cần):** hub `dym-setup` chỉ tốn một dòng context; thân workflow con được đọc khi gõ `/dym-setup <slug>`.
```bash
npx skills add rheinmir/dym            # project-scope (.claude/skills/) — hoặc thêm -g cho global
```
Rồi trong Claude Code: `/dym-setup` (bảng slug) · `/dym-setup install` · `/dym-setup ci` …

**Cách 2 — kéo bundle về đọc/sửa, symlink hub:**
```bash
git clone --depth 1 https://github.com/Rheinmir/dym.git doyourmagic-bundles
mkdir -p .claude/skills && ln -sfn ../../doyourmagic-bundles/setup/skills/dym-setup .claude/skills/dym-setup
```

Mở `setup/flow.html` (self-contained, `file://`) để xem sơ đồ luồng skill → sản phẩm → skill kế.

## Thêm bundle mới
Chạy `/doyourmagic <repo>` ở dự án bất kỳ → copy `doyourmagic/<repo>/` vào đây thành `<repo>/` → PR. Sub-skill muốn lên repo chính (`rheinmir/setup`, cài bằng `npx skills add rheinmir/setup#orca`) thì đi đường **Promote** trong skill `doyourmagic`.

## Quy ước tên
Mặc định `dym-<repo>-<slug>`; hub `dym-<repo>`. Có `--name <prefix>` và `--humanize` (xem skill). Hub đọc file con bằng đường tương đối `../<hub>-<slug>/SKILL.md` từ thư mục của chính nó — nên cài qua `npx skills add` hay symlink đều chạy.
