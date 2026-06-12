  # Hanbae Assets

  한배 앱에서 Firebase Remote Config로 운영하는 배너 및 광고 모달 이미지를 보관하는 public assets repository입니다.

  ## Directory Structure

  ```text
  hanbae-assets/
    banners/
      survey_feedback.png
      metronome_tutorial.png

    modals/
      wonkwang_university_2026_06.png
      survey_feedback_modal.png

    README.md
  ```

  ## Usage

  Firebase Remote Config의 image_url에는 GitHub page URL이 아니라 raw URL을 사용합니다.

  https://raw.githubusercontent.com/{owner}/hanbae-assets/main/{path}/{file_name}

  예시:

  https://raw.githubusercontent.com/{owner}/hanbae-assets/main/banners/survey_feedback.png

  https://raw.githubusercontent.com/{owner}/hanbae-assets/main/modals/wonkwang_university_2026_06.png

  ## Remote Config Examples

  ### Home Banners

  [
    {
      "id": "survey_feedback",
      "enabled": true,
      "image_url": "https://raw.githubusercontent.com/{owner}/hanbae-assets/main/banners/survey_feedback.png",
      "link_url": "https://forms.gle/..."
    }
  ]

  ### Home Ad Modals

  [
    {
      "id": "wonkwang_university_2026_06",
      "enabled": true,
      "image_url":
      "https://raw.githubusercontent.com/{owner}/hanbae-assets/main/modals/wonkwang_university_2026_06.png",
      "link_url": "https://example.com"
    }
  ]

  link_url이 없으면 생략하거나 빈 문자열로 둡니다.

  {
    "id": "survey_feedback_modal",
    "enabled": true,
    "image_url": "https://raw.githubusercontent.com/{owner}/hanbae-assets/main/modals/survey_feedback_modal.png"
  }

  ## Naming Rules

  파일명은 가능하면 Remote Config의 id와 동일하게 맞춥니다.

  id: survey_feedback_2026_06
  file: banners/survey_feedback_2026_06.png

  id: wonkwang_university_2026_06
  file: modals/wonkwang_university_2026_06.png

  ## Image Guidelines

  - Use png or jpg.
  - Use https URLs only.
  - Keep file size reasonably small.
  - Avoid private URLs or URLs that require authentication.
  - Do not use GitHub blob URLs.
  - Do not use Notion, Google Drive, or temporary attachment URLs for production.

  Recommended URL:

  https://raw.githubusercontent.com/{owner}/hanbae-assets/main/banners/example.png

  Do not use:

  https://github.com/{owner}/hanbae-assets/blob/main/banners/example.png

  ## Update Policy

  - 새 캠페인은 새 id와 새 파일명을 사용합니다.
  - 기존 캠페인의 단순 이미지 교체는 같은 파일명을 유지할 수 있습니다.
  - 이미 본 사용자에게 다시 노출해야 하는 광고 모달은 id를 새로 만듭니다.
  - Remote Config 배열 순서가 노출 순서입니다.
