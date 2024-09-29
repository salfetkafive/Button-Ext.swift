# Button+Ext.swift
Замена старому коду где используется `UIEdgeInsets` где warning:  `****** was deprecated in iOS 15.0: This property is ignored when using UIButtonConfiguration`

```swift
extension UIButton {
    /// Создает настроенную кнопку с заданными параметрами.
    ///
    /// - Parameters:
    ///   - icon: Имя изображения, которое будет использоваться в кнопке. По умолчанию - пустая строка (без изображения).
    ///   - title: Заголовок кнопки.
    ///   - fontSize: Размер шрифта заголовка кнопки. По умолчанию - 20.
    ///   - fontWeight: Вес шрифта заголовка кнопки. По умолчанию - `.bold`.
    ///   - foregroundColor: Цвет текста кнопки. По умолчанию - `.label`.
    ///   - backgroundColor: Фоновый цвет кнопки. По умолчанию - `.systemGray6`.
    ///   - cornerRadius: Радиус скругления углов кнопки. По умолчанию - 30.
    ///   - imagePadding: Расстояние между текстом и иконкой. По умолчанию - 10.
    ///   - imagePlacement: Положение иконки относительно текста. По умолчанию - `.leading` (слева от текста).
    ///   - buttonHeight: Высота кнопки. По умолчанию - 69.
    ///   - borderColor: Цвет обводки кнопки. По умолчанию - `.clear` (без обводки).
    ///   - borderWidth: Ширина обводки кнопки. По умолчанию - 0 (без обводки).
    ///
    /// - Returns: Настроенная кнопка `UIButton` с заданными параметрами.
    static func createButton(
        icon: String = "",
        title: String,
        fontSize: CGFloat = 20,
        fontWeight: UIFont.Weight = .bold,
        foregroundColor: UIColor = .label,
        backgroundColor: UIColor = .systemGray6,
        cornerRadius: CGFloat = 30,
        imagePadding: CGFloat = 10,
        imagePlacement: NSDirectionalRectEdge = .leading,
        buttonHeight: CGFloat = 69,
        borderColor: UIColor = .clear,
        borderWidth: CGFloat = 0
    ) -> UIButton {
        let button = UIButton(type: .system)

        // Создаем конфигурацию для кнопки
        var config = UIButton.Configuration.filled()
        config.baseForegroundColor = foregroundColor // Цвет текста
        config.baseBackgroundColor = backgroundColor // Фоновый цвет

        // Настройка текста
        config.title = title

        // Настройка шрифта
        let font = UIFont.systemFont(ofSize: fontSize, weight: fontWeight)
        config.attributedTitle = AttributedString(title, attributes: AttributeContainer([.font: font]))

        // Настройка изображения
        if let image = UIImage(named: icon) {
            config.image = image
            config.imagePadding = imagePadding // Расстояние между текстом и иконкой
            config.imagePlacement = imagePlacement // Положение иконки
        }

        // Применение конфигурации
        button.configuration = config
        button.layer.cornerRadius = cornerRadius
        button.layer.masksToBounds = true

        // Установка высоты кнопки
        button.heightAnchor.constraint(equalToConstant: buttonHeight).isActive = true

        // Настройка обводки
        button.layer.borderColor = borderColor.cgColor
        button.layer.borderWidth = borderWidth

        return button
    }
}
```

# Обращение
```swift
 var button = UIButton.createButton(icon: "NameIcon", title: "Hard")
```
Полное обращение
```swift
var button = UIButton.createButton(
        icon: String,
        title: String,
        fontSize: CGFloat,
        fontWeight: UIFont.Weight,
        foregroundColor: UIColor,
        backgroundColor: UIColor,
        cornerRadius: CGFloat,
        imagePadding: CGFloat,
        imagePlacement: NSDirectionalRectEdge,
        buttonHeight: CGFloat,
        borderColor: UIColor,
        borderWidth: CGFloat
    )
    
```




