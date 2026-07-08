students = {}

while True:
    print("\n=== 学生成绩管理系统 ===")
    print("1. 录入学生")
    print("2. 查询学生")
    print("3. 统计成绩")
    print("4. 显示所有")
    print("5. 退出")

    choice = input("请选择：")

    if choice == '1':
        sid = input("学号：")
        if sid in students:
            print("学号已存在")
            continue
        name = input("姓名：")
        scores = {}
        while True:
            subject = input("科目（输入0结束）：")
            if subject == '0':
                break
            score = float(input("成绩："))
            scores[subject] = score
        students[sid] = {'name': name, 'scores': scores}
        print("录入成功")

    elif choice == '2':
        sid = input("学号：")
        if sid not in students:
            print("未找到")
            continue
        stu = students[sid]
        print(f"姓名：{stu['name']}")
        for sub, sc in stu['scores'].items():
            print(f"{sub}: {sc}")
        if stu['scores']:
            scores = list(stu['scores'].values())
            print(f"平均分：{sum(scores) / len(scores):.1f}")

    elif choice == '3':
        all_scores = []
        for stu in students.values():
            all_scores.extend(stu['scores'].values())
        if all_scores:
            print(f"总人数：{len(students)}")
            print(f"最高分：{max(all_scores)}")
            print(f"最低分：{min(all_scores)}")
            print(f"平均分：{sum(all_scores) / len(all_scores):.1f}")

    elif choice == '4':
        for sid, stu in students.items():
            print(f"{sid} {stu['name']} {len(stu['scores'])}科")

    elif choice == '5':
        print("再见")
        break

    else:
        print("无效选择")
