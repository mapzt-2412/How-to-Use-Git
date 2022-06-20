- [1. Introduction](#1-introduction)
- [2. Working tree, repository,](#2-working-tree-repository)
- [3. Index definition](#3-index-definition)
- [4. Git tree, Branches](#4-git-tree-branches)
	- [4.1 Git tree](#41-git-tree)
	- [4.2 Branches](#42-branches)
- [5. Add, Commit, Merge, Stash](#5-add-commit-merge-stash)
	- [5.1 Git Add](#51-git-add)
	- [5.2 Git Commit](#52-git-commit)
	- [5.3 Git Merge](#53-git-merge)
	- [5.4 Git Stash](#54-git-stash)
- [6. Fetch, pull, push](#6-fetch-pull-push)
	- [6.1 Fetch](#61-fetch)
	- [6.2 Pull](#62-pull)
	- [6.3 Push](#63-push)
- [7. Pull/merge request](#7-pullmerge-request)
- [8. Conflict resolve when merge](#8-conflict-resolve-when-merge)
- [9. Conflict resolve when pull](#9-conflict-resolve-when-pull)
- [10. Reset, Revert](#10-reset-revert)
	- [10.1. Reset](#101-reset)
	- [10.2. Revert](#102-revert)
- [11. Gitlab, Github](#11-gitlab-github)
- [12. Other VSC tool](#12-other-vsc-tool)
- [13. Conventional commits](#13-conventional-commits)
- [14. Branching models](#14-branching-models)
	- [14.1 ](#141-git-add)
	- [14.2 ](#142-git-commit)
	- [14.3 GitLab Flow](#143-gitlab-flow)
	- [14.4 Trunk-based development](#144-trunk-based-development)
- [15. Submodule](#15-submodule)
- [16. Git tool, extension](#16-git-tool-extension)
# 1. Introduction
Git là 1 hệ thống quản lý phiên bản được các dev trên khắp thế giới sử dụng. Nó giúp bạn theo dõi những phiên bản khác nhau của code cũng như hợp tác với những dev khác
Nếu bạn đang phải OT trong 1 dự án nào đó, có thể bạn muốn theo dõi những điều chỉnh được thực hiện trên code, bởi ai, khi nào. Điều này càng trở nên quan trọng hơn nếu bạn gặp bug. Git có thể giúp đỡ bạn trong hoàn cảnh đó.
Vai trò của Git là cực kỳ quan trọng nếu như bạn muốn làm việc chung với những dev khác trong 1 dự án nào đó hoặc chính dự án của bạn.
# 2. Working tree, repository,
# 3. Index definition
# 4. Git tree, Branches
## 4.1 Git tree
+Git Tree là một dạng cấu trúc đồ thị có hướng dùng để xem lại lịch sử các commit của repository một cách trực quan. Trong đó, Git Tree bao gồm các nhánh đại diện cho các branches, mỗi một node là đại diện cho một lần commit.
Trong mỗi node commit sẽ chứa các thông tin liên quan đến lần commit này như commit id, author, message commit, thời gian commit,...
Nhờ có Git Tree, các developers có thể nắm bắt toàn bộ quá trình thay đổi, phân branches, gộp branches, các file đã thêm, đã xoá,... qua đó giúp quá trình quản lý file trong repo được tối ưu nhất có thể.</br>
+ Câu lệnh xem Git Tree: <code>git log –graph</code>
## 4.2 Branches
+ Git là hệ thống làm việc nhiều người. Nếu tất cả đều hoạt động chung một kho lưu trữ, những xung đột sẽ thường xuyên xảy ra (trùng tên file, tên lớp,...). Việc nhiều thành viên đảm nhận các công việc khác nhau và lưu trữ trong một kho chung sẽ rất khó quản lý, thiếu tính hệ thống và hiệu suất không cao.
+ Branch là nhánh ghi lại luồng lịch sử làm việc. Tương ứng với mỗi nhiệm vụ mà từng thành viên sẽ tạo một branch và làm việc trên branch đó. Sự phân nhánh này giúp các công việc của các thành viên trở nên có hệ thống và không làm ảnh hưởng đến branch khác, tiến hành đồng thời nhiều thay đổi trên một repo. Ta cũng có thể di chuyển qua lại giữa các branch.
+ Có hai loại branch: integration branch (branch tích hợp) và topic branch (branch chủ đề):
 + Integration branch: branch chính của dự án, có thể tạo ra bản phát hành. Được sử dụng như là nguồn phân branch nên cần duy trì trạng thái ổn định.
 + Topic branch: branch chủ đề, là branch tạo ra nhằm tiến hành công việc riêng biệt như chỉnh sửa lỗi, thêm chức năng,...
+ Các câu lệnh thao tác với branch:
 + <code>git branch</code>: liệt kê tất cả branch hiện có trong git repository.
 + <code>git branch<new_branch></code>: tạo branch mới có tên new_branch.
 + <code>git checkout<branch_name></code>: di chuyển đến branch có tên branch_name.
 + <code>git checkout -b<new_branch></code>: tạo branch mới có tên new_branch và di chuyển đến branch này.
 + <code>git branch -d<branch_name></code>: xóa branch có tên branch_name.
# 5. Add, Commit, Merge, Stash
## 5.1 Git Add
## 5.2 Git Commit
## 5.3 Git Merge
+ **Git Merge**:Tích hợp các thay đổi đã thực hiện trên các nhánh, thao tác này thường dùng để merge branch khác vào branch master trước khi push lên remote repository, hoặc merge hai branch thành một để giải quyết chung một task.
+ **Cách dùng:**
	+ <code>$ git merge <branch_name></code>
	+ hoặc <code>$ git merge <branch-name> <merged-branch-name></code>
+ **Merge non fast-forward**: Sẽ tạo ra một merge commit giúp cho việc tracking lịch sử nhánh.
	+ <code>$ git merge --no-ff bugfix <branch_name></code>
+ **Squash merge**: thêm option này vào ta có thể rút gọn các commit của nhánh merge thành 1 commit.
	+ <code>$ git merge –squash <branch_name></code>
	
## 5.4 Git Stash
+ **Git stash**: Được sử dụng khi muốn lưu lại các thay đổi chưa commit, thường rất hữu dụng khi bạn muốn đổi sang 1 branch khác khi đang làm dở ở branch hiện tại.
+ **Git stash save**: Để lưu lại toàn bộ nội dung công việc đang làm dở
	+ <code>$ git stash save</code>
	+ hoặc <code>$ git stash</code>
+ **Git stash list** Để xem lại danh sách các stash đã lưu
	+ <code>$ git stash list</code>
+ Để xem cả nội dung thay đổi của từng stash đã lưu trong danh sách thì thêm **option -p**
	+ <code>$ git stash list -p</code>
+ **Git stash show <stash-name>**: Để xem nội dung thay đổi của một stash đã lưu
	+ <code>$ git stash show stash@{1}</code>
+ **Git stash apply <stash-name>**: Để apply lại thay đổi từ một stash đã lưu
	+ <code>$ git stash apply stash@{1}</code>
+ **Git stash drop <stash-name>**: Để xóa một stash đã lưu
	+ <code>$ git stash drop stash@{1}</code>
+ Với stash được lưu với ý định không dùng lại nhiều hơn 1 lần thì thường nó sẽ được xóa đi ngay khi được apply.
	+ <code>$ git stash apply stash@{1}</code>
	+ <code>$ git stash drop stash@{1}</code>
+ hoặc đơn giản hơn thì dùng
	+ <code>$ git stash pop stash@{1}</code>
+ **Git stash clear**: Để xoá toàn bộ stack đã lưu
	+ <code>$ git stash clear</code>

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
Pull request được tạo ra để đưa những file source code lên 1 host chung nơi mọi người có quyền truy cập sẽ truy cập vào và cùng review, để lại comment trên những file source code đó.

Quá trình phát triển với pull request:
- Clone hoặc pull source code
- Tạo nhánh làm việc
- Thực hiện các thay đổi như thêm và chỉnh sửa các hàm,...
- Push sau khi đã hoàn thành
- Kiểm tra những thay đổi từ pull request được thông báo
- Review và gửi phản hồi
- Merge nếu không có vấn đề
- Đóng pull request

Tạo pull request:
- Click New Pull Request 
![image](https://user-images.githubusercontent.com/59039313/174484034-0f298f81-aaac-48ae-ab1c-54331ba585da.png)
- Chọn nhánh muốn merger với nhánh khác và Click Create Pull Request
![image](https://user-images.githubusercontent.com/59039313/174484151-2ceb094b-050b-4b93-ad23-62c64988b77b.png)
- Thêm Title và Description cho Pull Request
![image](https://user-images.githubusercontent.com/59039313/174484210-8132ed86-3932-4e5e-b1be-3c1fd22cbf2d.png)
- Click Files Changed để xem những thay đổi của file. Để lại review về file
![image](https://user-images.githubusercontent.com/59039313/174484313-46c377ed-9487-4c9a-9a6f-8e0dada89876.png)
- Để lại Comment hoặc là Merge pull quest và đóng pull request
![image](https://user-images.githubusercontent.com/59039313/174484355-1b990958-ef90-4330-b58e-d9afb09c3fe3.png)


**Merge Request**
- Merge Request tương tự như Pull Request nhưng được sử dụng trong GitLab còn Pull Request được sử dụng trong GitHub

Tạo Merge Request:
- Chọn Merge Request và chọn New merge request
![image](https://user-images.githubusercontent.com/59039313/174484722-3f43dc44-8f52-4ee4-b6a0-d76d093b2f87.png)
- Chọn source và target branch và chọn Compare branches and continue
![image](https://user-images.githubusercontent.com/59039313/174484758-c422ec39-8ea2-40e2-abeb-51f29c92f237.png)
- Điền các Fields và click Create merge request
# 8. Conflict resolve when merge
- Trong một hệ thống kiểm soát nguồn như Git, xung đột có thể xảy ra khi hai hoặc nhiều người thay đổi cùng một file. Lúc này Git sẽ không biết phải chọn phiên bản nào nên dẫn đến xung đột. Các xung đột có thể xuất hiện tại local repo hoặc remote repo.
- Khi xung đột xảy ra, Git sẽ đánh dấu file bị xung đột và tạm dừng quá trình merge. Sau đó, trách nhiệm của dev là giải quyết xung đột dựa trên những gì Git đã đánh dấu.
- Cách trực tiếp nhất để giải quyết xung đột khi merge là chỉnh sửa file bị xung đột sau đó thực hiện add, commit như bình thường.
# 9. Conflict resolve when pull
Khi thực hiện pull, conflict sẽ xảy ra khi:
-Sửa đổi một tệp trong thư mục làm việc và commit
-Sửa đổi một tệp trong kho lưu trữ từ xa và commit
-Thực hiện git pull => Sẽ xảy ra xung đột
# 10. Reset, Revert
## 10.1. Reset
- Khi chúng ta làm sai ở một vài commit gần và muốn quay trở lại để thay đổi toàn bộ những thay đổi trong những commit trước đó. Thì chúng ta nên sử dụng reset.
- Git reset được sử dụng để quay lại một điểm commit nhất định và xóa lịch sử của các lần commit trước đó.
- `git reset [--mixed | --soft | --hard | --merge | --keep] [-q] [<commit>]`
- `git reset --soft [<commit>]` : Chi thay đổi commit history.
- `git reset --mixed [<commit>]` : Thay đổi commit history và index.
- `git reset --hard [<commit>]` : Xóa hoàn toàn các commit.
- `git reset --merge [<commit>]` : Giống như `hard` nhưng không thực hiện khi có thay đổi mới mà chưa commit trên worktree và index.
- `git reset --keep [<commit>]` : giống như `hard` nhưng khi có thay đổi trên index thì sẽ không được thực hiện.



https://user-images.githubusercontent.com/73237028/174479721-37ab87eb-885f-4a0d-84da-f5feee7f3048.mp4



- Một vài trường hợp dùng git reset khác :
  - Nếu bạn đã dùng lệnh git add để cập nhật thay đổi vào vùng staging, bạn có thể hủy thao tác này bằng cách thực hiện lệnh:
	```git
	git reset
	```
  - Nếu muốn hủy một file nào đó trong vùng staging chứ không phải toàn bộ thì dùng lệnh
	```git
	git reset -- filename
	```
## 10.2. Revert
- Revert được giống trong trường hợp giống reset nhưng cách thức hoạt động nó khác nhau. Revet thì không xóa các commit như reset mà nó sẽ tạo thêm 1 commit mới và giống với commit mà muốn thay đổi và chỉ động đến file cần thay đổi không liên quan đến file khác.
- `git revert [--[no-]edit] [-n] [-m parent-number] [<commit>]
`
- `<commit>`: Tùy chọn commit được sử dụng để revert một commit. Để revert một commit, chúng ta cần id tham chiếu commit.
- `<–edit>`: Nó được sử dụng để chỉnh sửa tin nhắn commit trước khi revert  commit. 
- `-m parent-number / – mainline parent-number`: nó được sử dụng để hoàn lại việc hợp nhất(merge). Nói chung, chúng ta không thể hoàn lại một hợp nhất(merge) vì chúng ta không biết mặt nào của hợp nhất(merge) nên được coi là nhánh chính để merge. Chúng ta có thể chỉ định parent-number và cho phép hoàn lại để đảo ngược thay đổi liên quan đến parent đã chỉ định.
- `-n / – no-commit`: Nói chung, đây là lệnh hoàn lại commit theo mặc định. Tùy chọn không commit sẽ không tự động commit. Ngoài ra, nếu tùy chọn này được sử dụng, chỉ mục(index) của bạn không phải khớp với commit HEAD.

https://user-images.githubusercontent.com/73237028/174479676-7e583204-200a-472e-8b44-691849e5a273.mp4



# 11. Gitlab, Github
+ GitLab là một trình quản lý kho Git dựa trên Internet. Đó là một máy chủ đơn giản, hiện đại. GitLab là một mã nguồn mở và hoàn toàn miễn phí, cung cấp công cụ quản lý dự án như Heat Tracker, Nhóm giai đoạn, Vấn đề, Lộ trình,... 
để đơn giản hoá quy trình làm việc hợp tác cho toàn bộ chu trình phát triển phần mềm. Đây là cách hiệu quả để lưu trữ trên máy chủ, người dùng có thể kiểm soát và quản lý. Giống với GitHub, nhưng có vài tính năng bổ sung như GitHub, Google Code, Bitbucket… 
+ Github là một dịch vụ quản lý kho dựa trên web và kho lưu trữ mã nguồn lớn nhất trên thế giới. 
Là nơi tập hợp một trong những nhà phát triển lớn nhất để hợp tác với các dự án phát triển phần mềm. 
Đây là kho lưu trữ mã lớn nhất thế giới cho phép người dùng phát triển, chia sẻ và đóng góp các dự án nguồn mở được viết bằng hơn 300 ngôn ngữ lập trình độc đáo. 
Đây là nơi quan trọng để phát triển phần mềm, dịch vụ lý tưởng cho hợp tác làm việc nhóm giữa các developers cũng như cải thiện quy trình phát triển phần mềm.

|                     GitLab                      |                        GitHub                        |
| :---------------------------------------------: | :--------------------------------------------------: |
|               Owned by GitLab Inc               |            Owned by Microsoft Corporation            |
|        Open-source for community edition        |                   Not open-source                    |
| Provides user to see project development charts | Doesn't have charts yet but can check commit history |

# 12. Other VSC tool
|                           Git                           |          Concurrent version system (CVS)          |
| :-----------------------------------------------------: | :-----------------------------------------------: |
|                     Distributed vsc                     |                  Centralized vsc                  |
|                  Operations are atomic                  |             Operations are not atomic             |
|                 Changes are per project                 |               Changes are per file                |
|                Have index (staging area)                |                 Do not have index                 |
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
## 14.1
## 14.2
## 14.3 GitLab Flow
+ **GitLab Flow** là một giải pháp thay thế đơn giản hơn cho Git workflow, kết hợp phát triển theo hướng tính năng và phân nhánh tính năng với theo dõi vấn đề. Với GitFlow, các nhà phát triển tạo nhánh develop và đặt nhánh đó làm mặc định trong khi GitLab Flow hoạt động với nhánh chính từ đầu. GitLab flow thì xoay quanh các nhánh môi trường production, staging...
+ GitLab Flow phù hợp khi ta muốn giữ nhiều môi trường và muốn có 1 môi trường staging tách với môi trường production. Như vậy khi nào nhánh main có thể triển khai, ta có thể merge với nhánh production và phát hành nó.
			![](https://www.flagship.io/wp-content/uploads/gitlab_flow_environment_branches.png)
+ GitLab Flow phù hợp với tình huống mà ta không thể kiểm soát được thời gian ra mắt sản phẩm, ví dụ như khi một ứng dụng iOS cần được App Store xác thực trước hay như khi ta có các deployment window cụ thể.

## 14.4 Trunk-based development
+ **Trunk-based development**: Core concept của giải pháp này là trunk (thân cây) thay vì nhánh như các mô hình khác. Trong mô hình này tất cả mọi người sẽ commit vào một nhánh chính duy nhất (trunk) thay vì nhiều nhánh cho các tính năng hoặc môi trường khác nhau.
+ **Tích hợp liên tục (CI) và phân phối liên tục (CD)** là 2 yếu tố quan trọng trong Trunk-based development, vì các thay đổi luôn được thực hiện ở trên Trunk. 
+ **CI** là phương pháp phát triển phần mềm yêu cầu các thành viên của team tích hợp công việc của họ thường xuyên, mỗi ngày ít nhất một lần. Mỗi tích hợp được "build" tự động (bao gồm cả test) nhằm phát hiện lỗi nhanh nhất có thể. Cách tiếp cận này giảm thiểu vấn đề tích hợp và cho phép phát triển phần mềm nhanh hơn. Một kịch bản CI bắt đầu bằng việc developer commit code lên repository. Các bước trong một kịch bản CI thường như sau:
	1 Đầu tiên, developer commit code lên repo.
	2 CI server giám sát repo và kiểm tra xem liệu có thay đổi nào trên repo hay không (liên tục, chẳng hạn mỗi phút 1 lần)
	3 Ngay khi commit xảy ra, CI server phát hiện repo có thay đổi, nên nó nhận code mới nhất từ repo và sau đó build, chạy unit và integration test
	4 CI server sẽ sinh ra các feedback và gửi đến các member của project
	5 CI server tiếp tục chờ thay đổi ở repo
+ **CD** là hướng tiếp cận để phát hành phần mềm, team sẽ liên tục phát hành các sản phẩm chất lượng thông qua 1 chuỗi kiểm thử tự động. Bằng cách triển khai tất cả thay đổi về code (đã được build và test) đến môi trường testing hoặc staging. CD cho phép developer tự động hóa phần testing bên cạnh việc sử dụng unit test, kiểm tra phần mềm qua nhiều thước đo trước khi triển khai cho khách hàng. 
+ Lợi ích rõ ràng nhất là thời gian tiếp thị nhanh hơn vì code luôn sẵn sàng được triển khai cho người dùng. Nhóm nhận được phản hồi liên tục về sản phẩm từ người dùng và sau đó kết hợp phản hồi này vào bản phát hành tiếp theo.
			![](https://www.flagship.io/wp-content/uploads/trunk-based-development-branching-strategy.png)
> “Branches create distance between developers and we do not want that” — Frank Compagner, Guerrilla Games.
+ Khoảng cách ở đây là về khoảng cách để tích hợp code từ nhiều components/modules/sub-teams thành một mã nhị phân để có thể triển khai. Những vấn đề về khoảng cách có thể là:
	+ Làm hỏng 1 đoạn nào đó không lường trước được khi merge
	+ Sự khó khăn khi merge
	+ Không cho thấy rõ các việc bị trùng lặp cho tới khi được merge
	+ Không cho thấy các vấn đề như code không tương thích nếu không làm hỏng build
+ Trunk-based development là mô hình phân nhánh giảm thiểu các vấn đề này xuống tối thiểu.
+ Một quy tắc chính là Trunk-Based Development teams hoặc là phát hành trực tiếp từ trunk, hoặc là họ tạo một nhánh từ trunk chỉ riêng cho việc phát hành.

# 15. Submodule
- Trong môi trường phát triển phần mềm, phát triển các dự án lớn, chúng ta không thể gộp tất cả vào một repository trên gitlab hay github được, mà chia thành nhiều module lớn nhỏ khác nhau rồi trong project chính sẽ tiến hành clone source từ các module đó về để chạy.
- Để thêm một submodule vào project ta sử dụng:
  - `$ git submodule add <repository> [<path>]`
- Khi cần cập nhập module, ta dùng lệnh :
  - `$ git submodule update [--init]`
  - Lựa chọn --init sẽ cho phép ta cập nhập các module chưa được lấy về. Ví như ở máy tính của bạn, bạn chạy lệnh add để lấy repo về rồi, thì không cần --init nữa. Còn ở các máy tính khác, repo chưa được lấy về, thì ta cần phải thêm lựa chọn này. Tức là repo phải có sẵn trong máy rồi mới update được.
- Ngoài ra, với các dự án mới khi được tải về thì các module sẽ không tự động tải về mà ta phải tải repo chính rồi chạy lệnh cập nhập thì mới được. Tuy nhiên, sự thật không phũ phàng tới vậy, ngay ở lệnh tải về ta có thể lấy ngay được về các module với lựa chọn --recursive
- `$ git clone --recursive <repository> `
- Ưu điểm
  - Hạn chế sai sót, thiếu sót mỗi khi cần thêm hay cập nhật gì
  - Có thể chỉnh sửa code trong submodule từ các module con rồi push thẳng lên chứ ko cần phải vào đúng repo của submodule mới sửa được rồi push lên, rồi mấy module kia mới được pull về.
  - Đỡ tốn thời gian xóa rồi import/add reference thư viện lại
- Nhược điểm
  - Luôn phải pull submodule sau khi có thay đổi gì đó trên submodule (nhưng nếu setup recursive thì khỏi lo)
  - Chiếm dung lượng ổ cứng do khi pull code về thì trong mỗi module đều phải có thư mục code của thư viện chung đó


https://user-images.githubusercontent.com/73237028/174479487-a30c600f-b34b-4bea-8a2c-40388021d1d4.mp4

# 16. Git tool, extension

**GitHub Desktop**
- Là ứng dụng cho phép tương tác với github vằng GUI thay vì dòng lệnh hoặc trình duyệt web.
- Có thể sử dụng Github Desktop để hoàn thành các lệnh git từ màn hình với xác nhận trực quan về thay đổi
- Có thể push, pull và clone remote repository với github desktop và sử dụng các công cụ như phân bổ commits và tạo pull request

**SourceTree**
- Công cụ trực quan hóa cho GIT trên Windows/ macOS
- Phục vụ như sự thay thế thuận tiện cho việc sử dụng Command Prompt để thực hiện các lệnh GIT
- Có giao diện thân thiện với người dùng trực quan cho phép ngay cả những người dùng GIT thiếu kinh nghiệm cũng có thể tham gia đầy đủ vào toàn bộ quy trình làm việc cộng tác.
