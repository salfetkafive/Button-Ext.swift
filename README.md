# Button+Ext.swift
```swift
extension UIButton {
    static func createButton(icon: String = "", title: String) -> UIButton {
        let button = UIButton(type: .system)
        
        // Создаем конфигурацию для кнопки
        var config = UIButton.Configuration.filled()
        config.baseForegroundColor = .label // Цвет текста
        config.baseBackgroundColor = UIColor.systemGray6

        // Настройка текста
        config.title = title
        
        // Настройка шрифта
        let font = UIFont.systemFont(ofSize: 20, weight: .bold)
        config.attributedTitle = AttributedString(title, attributes: AttributeContainer([.font: font]))
        
        // Настройка изображения
        if let image = UIImage(named: icon) {
            config.image = image
            config.imagePadding = 10 // Расстояние между текстом и иконкой
            config.imagePlacement = .leading // Иконка слева от текста
        }

        // Применение конфигурации
        button.configuration = config
        button.layer.cornerRadius = 30
        button.layer.masksToBounds = true
         
        button.heightAnchor.constraint(equalToConstant: 69).isActive = true
        
        return button
    } 
}
```
