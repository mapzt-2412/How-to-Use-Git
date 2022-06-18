- [1. Introduction](#1-introduction)
- [2. Working tree, repository,](#2-working-tree-repository)
- [3. Index definition](#3-index-definition)
- [4. Git tree, Branches](#4-git-tree-branches)
- [5. Add, Commit, Merge, Stash](#5-add-commit-merge-stash)
- [6. Fetch, pull, push](#6-fetch-pull-push)
- [7. Pull/merge request](#7-pullmerge-request)
- [8. Conflict resolve when merge](#8-conflict-resolve-when-merge)
- [9. Conflict resolve when pull](#9-conflict-resolve-when-pull)
- [10. Revert, Reset](#10-revert-reset)
- [11. Gitlab, Github](#11-gitlab-github)
- [12. Other VSC tool](#12-other-vsc-tool)
- [13. Conventional commits](#13-conventional-commits)
- [14. Branching models](#14-branching-models)
- [15. Submodule](#15-submodule)
- [16. Git tool, extension](#16-git-tool-extension)
# 1. Introduction
Git là 1 hệ thống quản lý phiên bản được các dev trên khắp thế giới sử dụng. Nó giúp bạn theo dõi những phiên bản khác nhau của code cũng như hợp tác với những dev khác
Nếu bạn đang phải OT trong 1 dự án nào đó, có thể bạn muốn theo dõi những điều chỉnh được thực hiện trên code, bởi ai, khi nào. Điều này càng trở nên quan trọng hơn nếu bạn gặp bug. Git có thể giúp đỡ bạn trong hoàn cảnh đó.
Vai trò của Git là cực kỳ quan trọng nếu như bạn muốn làm việc chung với những dev khác trong 1 dự án nào đó hoặc chính dự án của bạn.
# 2. Working tree, repository,
# 3. Index definition
# 4. Git tree, Branches
# 5. Add, Commit, Merge, Stash
# 6. Fetch, pull, push
## 6.1 Fetch
+ Downloads all the latest commits from all branches and also all the new branches from the remote and saves it in the local repo
+ But it will not merge it to the local branch that are active
+ It is useful to review changes in the remote repo before pulling
 ## 6.2 Pull
 + Updates your current local working branch, and all of the remote tracking branches.
 + However, will merge all changes into local working directory (might create merge conflict)
 ## 6.3 Push
 + Updates the remote branch with local commits
 + By default, git push only updates the corresponding branch on the remote.
 + It is good practice to fetch or pull before pushing to avoid conflict
 > Common push options
 + git push -u <remote_name> [branch] : Useful when pushing a new branch, this creates an upstream tracking branch with a lasting relationship to your local branch

 + git push --all: push all branches

 + git push <remote_name> --delete <branch_name>  
  => can be used to delete a remote branch
 


# 7. Pull/merge request
# 8. Conflict resolve when merge
# 9. Conflict resolve when pull
Khi thực hiện pull, conflict sẽ xảy ra khi:
-Sửa đổi một tệp trong thư mục làm việc và commit
-Sửa đổi một tệp trong kho lưu trữ từ xa và commit
-Thực hiện git pull => Sẽ xảy ra xung đột
# 10. Revert, Reset
# 11. Gitlab, Github
# 12. Other VSC tool
|                           Git                           |          Concurrent version system (CVS)          |
|:-------------------------------------------------------:|:-------------------------------------------------:|
| Distributed vsc                                         | Centralized vsc                                   |
| Operations are atomic                                   | Operations are not atomic                         |
| Changes are per project                                 | Changes are per file                              |
| Have index (staging area)                               | Do not have index                                 |
| The repository are committed into the local repository. | The repository are committed into central server. |
# 13. Conventional commits
Conventional Commits là một bộ quy tắc viết commit message sinh ra với mục đích để cả người đọc được và các công cụ máy tính có thể tìm kiếm. Nó cung cấp một bộ quy tắc dễ dàng để tạo lịch sử commit rõ ràng.
CC có thể viết dưới dạng:
		<type>[optional scope]: <description>
  			  [optional body]
  			  [optional footer(s)]
Các thành phần type, description là bắt buộc cần có trong commit message, optional là tùy chọn có hoặc không có cũng được

type: từ khóa để phân loại commit là feature, fix bug, refactor.
scope: cũng được dùng để phân loại commit, vùng ảnh hưởng của commit, trả lời câu hỏi: commit này refactor|fix cái gì? được đặt trong cặp ngoặc đơn ngay sau type. VD: feat(authentication):, fix(parser):
description: là mô tả ngắn về những gì sẽ bị sửa đổi trong commit đấy
body: là mô tả dài và chi tiết hơn, cần thiết khi description chưa thể nói rõ hết được, có thể thêm phần ghi chú bằng các keyword
footer: một số thông tin mở rộng như số ID của pull request, issue.. được quy định theo conventional

Một số type phổ biến như: feat, fix, refactor, docs,....
Examples:
feat(lang): add English language
fix: fix header dashboard page
fix: prevent racing of requests
Introduce a request id and a reference to the latest request. Dismiss incoming responses other than from the latest request.
Refs: #123
# 14. Branching models
# 15. Submodule
# 16. Git tool, extension
