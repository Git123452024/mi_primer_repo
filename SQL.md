---- crear vista dinamica de toda una base de datos, uniendola las tablas
SET @schema_name = 'data';
SET @view_name = 'Venta23'; -- Puedes proporcionar un nombre personalizado aquí

-- Dynamic SQL to create a view
SET @sql = NULL;
SELECT GROUP_CONCAT('SELECT * FROM ', table_name SEPARATOR ' UNION ')
INTO @sql
FROM information_schema.tables
WHERE table_schema = @schema_name;

-- Create the view
SET @create_view_sql = CONCAT('CREATE VIEW ', @schema_name, '.', @view_name, ' AS ', @sql);
PREPARE stmt FROM @create_view_sql;
EXECUTE stmt;
DEALLOCATE PREPARE stmt;
