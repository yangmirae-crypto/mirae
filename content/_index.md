---
title: 'Mirae Yang | 라이프스타일 멘토 & 비즈니스 오너'
date: 2026-07-02
type: landing

sections:
  - block: hero
    content:
      title: "건강한 일상과 내일의 성장을 돕는 라이프스타일 멘토, Mirae Yang입니다."
      text: "나를 세우고 타인을 돕는 삶, 당신의 긍정적인 변화를 돕습니다."
      primary_action:
        text: "커뮤니티 참여하기"
        url: "#contact"
        icon: users
        style: gradient
      trust:
        stars: 5
        text: "함께 성장하고 나누는 라이프스타일 커뮤니티"
    design:
      spacing:
        padding: ["6rem", 0, "6rem", 0]
      background:
        color: "#FCF8F5"
        gradient:
          type: linear
          angle: 135
          start: "rgba(224,90,71,0.15)" # Sunrise Coral
          end: "rgba(210,145,188,0.15)" # Lilac

  - block: markdown
    id: about
    content:
      title: "🙋 소개"
      subtitle: "About Mirae Yang"
      text: |
        돌봄의 현장, 그리고 비즈니스 영역을 넘나들며 사람들의 긍정적인 변화를 돕고 있습니다. 좋은 영양과 건강한 습관, 그리고 꾸준한 독서와 배움을 통해 얻은 통찰을 나눕니다. 
        
        **&lt;더불어 사는 자본주의&gt;**의 철학처럼, 누구나 자신만의 가치를 세우고 타인에게 선한 영향력을 발휘할 수 있도록 당신의 여정에 든든한 파트너가 되어 드립니다.
    design:
      spacing:
        padding: ["5rem", 0, "5rem", 0]

  - block: features
    id: activities
    content:
      subtitle: "활동 / 포트폴리오"
      title: "🗂️ 주요 활동 및 나눔"
      text: "삶을 아름답게 가꾸고, 따뜻한 마음을 나누는 다양한 활동들입니다."
      items:
        - name: "성경 말씀 카드 제작 및 나눔"
          icon: heart
          description: "삶의 지혜와 위로가 담긴 구절을 따뜻한 풍경과 조화롭게 디자인하여, 주변 사람들에게 긍정적인 에너지와 마음을 전하는 나눔 활동."
        - name: "발렌타인 홈 콘서트 기획"
          icon: musical-note
          description: "따뜻한 커뮤니티 모임을 위한 프로그램 기획 및 맞춤형 초청장 디자인 주관."
        - name: "디지털 메시지 디자인"
          icon: paint-brush
          description: "불필요한 장식을 덜어내어 가독성을 높이고, 전하고자 하는 핵심 메시지와 자연의 아름다움에 집중한 맞춤형 초청장 및 시각 자료 제작."
    design:
      layout: grid
      css_class: "bg-gradient-to-br from-[#FCF8F5] via-[#FFF5F5] to-[#FBF3F9]"
      spacing:
        padding: ["5rem", 0, "5rem", 0]

  - block: features
    id: services
    content:
      subtitle: "서비스 및 가이드"
      title: "🧰 서비스 및 커뮤니티 안내"
      text: "건강하고 풍요로운 삶의 성장을 돕기 위해 준비된 프로그램입니다."
      items:
        - name: "건강 라이프스타일 멘토링"
          icon: bolt
          description: "영양학적 지식을 바탕으로 일상 속 건강한 습관과 맞춤형 라이프스타일 가이드 제공."
        - name: "자기 계발 북클럽 리딩"
          icon: book-open
          description: "성공의 원칙을 함께 읽고 나누며, 각자의 목표를 향해 나아갈 수 있도록 돕는 긍정적인 독서 모임 운영."
    design:
      layout: grid
      spacing:
        padding: ["5rem", 0, "5rem", 0]

  - block: content-collection
    id: blog
    content:
      subtitle: "최근 글"
      title: "✍️ 블로그"
      text: "건강, 영양 및 자기 계발에 관한 다양한 정보와 글을 나눕니다."
      page_type: blog
      count: 2
      archive:
        enable: true
        text: "전체 글 보기"
    design:
      view: card
      columns: 2
      css_class: "bg-gradient-to-br from-[#FCF8F5] via-[#FFF5F5] to-[#FBF3F9]"
      spacing:
        padding: ["5rem", 0, "5rem", 0]

  - block: testimonials
    id: testimonials
    content:
      subtitle: "후기"
      title: "💬 추천사 및 참여자 후기"
      items:
        - name: "독서 모임 멤버"
          role: "북클럽 참여자"
          text: "함께 <더불어 사는 자본주의>를 읽고 나누며 제 삶의 방향이 긍정적으로 바뀌었어요. 늘 따뜻하게 이끌어주셔서 감사합니다."
        - name: "행사 참석자"
          role: "홈 콘서트 참석자"
          text: "초청장을 받았을 때부터 감동이었습니다. 따뜻한 계절의 풍경만으로도 진심이 전해지더라고요."
        - name: "멘토링 참여자"
          role: "라이프스타일 멘토링 멤버"
          text: "제게 꼭 맞는 건강 습관을 섬세하게 짚어주셔서 하루하루가 활기찹니다."
    design:
      spacing:
        padding: ["5rem", 0, "5rem", 0]

  - block: faq
    id: faq
    content:
      subtitle: "자주 묻는 질문"
      title: "❓ FAQ"
      items:
        - question: "독서 모임이나 멘토링은 누구나 참여할 수 있나요?"
          answer: "네, 더 나은 삶과 건강한 성장에 관심 있는 분이라면 누구나 환영합니다."
        - question: "신청은 어떻게 진행되나요?"
          answer: "하단의 문의 폼이나 연락처로 남겨주시면 편하신 시간과 참여 방법을 안내해 드립니다."
    design:
      css_class: "bg-gradient-to-br from-[#FCF8F5] via-[#FFF5F5] to-[#FBF3F9]"
      spacing:
        padding: ["5rem", 0, "5rem", 0]

  - block: contact-info
    id: contact
    content:
      subtitle: "통합 문의"
      title: "✉️ 연락처 및 예약/신청"
      text: "건강 멘토링, 북클럽 참여 등 문의가 있거나 신청을 원하시면 아래 정보를 이용하거나 폼을 작성해 주세요."
      email: "yangmirae@gmail.com"
      phone: "201-315-8424"
      address:
        lines:
          - "활동 지역: New City, NY 및 뉴저지 일대"
      show_form: true
      form_action: "#"
    design:
      spacing:
        padding: ["5rem", 0, "5rem", 0]
---
